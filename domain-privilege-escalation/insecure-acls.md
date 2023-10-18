# Abusing ACLs

* `ForceChangePassword` abused with `Set-DomainUserPassword`
* `Add Members` abused with `Add-DomainGroupMember`
* `GenericAll` abused with `Set-DomainUserPassword` or `Add-DomainGroupMember`
* `GenericWrite` abused with `Set-DomainObject`
* `WriteOwner` abused with `Set-DomainObjectOwner`
* `WriteDACL` abused with `Add-DomainObjectACL`
* `AllExtendedRights` abused with `Set-DomainUserPassword` or `Add-DomainGroupMember`
* `Addself` abused with `Add-DomainGroupMember`

<figure><img src="../.gitbook/assets/ACL_attacks_graphic.png" alt=""><figcaption></figcaption></figure>

ACL attacks:

* [ForceChangePassword](https://bloodhound.readthedocs.io/en/latest/data-analysis/edges.html#forcechangepassword) - gives us the right to reset a user's password without first knowing their password (should be used cautiously and typically best to consult our client before resetting passwords).
* [GenericWrite](https://bloodhound.readthedocs.io/en/latest/data-analysis/edges.html#genericwrite) - gives us the right to write to any non-protected attribute on an object. If we have this access over a user, we could assign them an SPN and perform a Kerberoasting attack (which relies on the target account having a weak password set). Over a group means we could add ourselves or another security principal to a given group. Finally, if we have this access over a computer object, we could perform a resource-based constrained delegation attack which is outside the scope of this module.
* `AddSelf` - shows security groups that a user can add themselves to.
* [GenericAll](https://bloodhound.readthedocs.io/en/latest/data-analysis/edges.html#genericall) - this grants us full control over a target object. Again, depending on if this is granted over a user or group, we could modify group membership, force change a password, or perform a targeted Kerberoasting attack. If we have this access over a computer object and the Local Administrator Password Solution (LAPS) is in use in the environment, we can read the LAPS password and gain local admin access to the machine which may aid us in lateral movement or privilege escalation in the domain if we can obtain privileged controls or gain some sort of privileged access.

Some common attack scenarios may include:

| Attack                                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Abusing forgot password permissions` | Help Desk and other IT users are often granted permission to perform password resets and other privileged tasks. If we can take over an account with these privileges (or an account in a group that confers these privileges on its users), we may be able to perform a password reset for a more privileged account in the domain.                                                                                                                                                 |
| `Abusing group membership management` | It's also common to see Help Desk and other staff that have the right to add/remove users from a given group. It is always worth enumerating this further, as sometimes we may be able to add an account that we control into a privileged built-in AD group or a group that grants us some sort of interesting privilege.                                                                                                                                                           |
| `Excessive user rights`               | We also commonly see user, computer, and group objects with excessive rights that a client is likely unaware of. This could occur after some sort of software install (Exchange, for example, adds many ACL changes into the environment at install time) or some kind of legacy or accidental configuration that gives a user unintended rights. Sometimes we may take over an account that was given certain rights out of convenience or to solve a nagging problem more quickly. |

## ACL Enumeration

```
PS C:\rfs> Find-InterestingDomainAcl
```

```powershell
PS C:\htb> Import-Module .\PowerView.ps1
PS C:\htb> $sid = Convert-NameToSid wley
PS C:\htb> Get-DomainObjectACL -Identity * | ? {$_.SecurityIdentifier -eq $sid}
```

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

{% code overflow="wrap" %}
```powershell
PS C:\htb> $guid= "00299570-246d-11d0-a768-00aa006e0529"
PS C:\htb> Get-ADObject -SearchBase "CN=Extended-Rights,$((Get-ADRootDSE).ConfigurationNamingContext)" -Filter {ObjectClass -like 'ControlAccessRight'} -Properties * |Select Name,DisplayName,DistinguishedName,rightsGuid| ?{$_.rightsGuid -eq $guid} | fl

```
{% endcode %}
