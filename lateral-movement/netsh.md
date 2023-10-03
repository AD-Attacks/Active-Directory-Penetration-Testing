# NetSH

### Windows netsh Port Forwarding

{% code overflow="wrap" %}
```powershell
netsh interface portproxy add v4tov4 listenport=3340 listenaddress=10.1.1.110 connectport=3389 connectaddress=10.1.1.110
```
{% endcode %}

{% code overflow="wrap" %}
```powershell
netsh interface portproxy add v4tov4 listenport=4545 connectaddress=192.168.50.44 connectport=4545
```
{% endcode %}

{% code overflow="wrap" %}
```powershell
netsh advfirewall firewall add rule name="PortForwarding 80" dir=in action=allow protocol=TCP localport=80
```
{% endcode %}
