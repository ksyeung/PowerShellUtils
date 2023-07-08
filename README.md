# PowerShellUtils
Miscellaneous PS scripts for later inclusion into an incident response tool that looks up malware samples by various hashes (SHA1, SHA256, MD5, humanhash, imphash, ssdeep, TLSH), URLs, IP addrs, domains, other IOCs

ImportHash.ps1 (in progress):
Creates a hash based on imported library names, see https://www.mandiant.com/resources/blog/tracking-malware-import-hashing

ImportHash.ps1 notes:
The ordinal lookup function needs testing
This script has yet to be refactored according to this [style guide](https://github.com/mattifestation/PowerShellArsenal/tree/master#script-style-guide)
Thanks to @mattifestation for writing the PowerShell PE parser, Get-PE1.py

Example use:
~~~
$importHash = Get-ImpHash -path ".\notepad.exe"
Write-Output $importHash
~~~
