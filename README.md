# PowerShellUtils
Miscellaneous PS scripts for later inclusion into an incident response tool that looks up malware samples by various hashes (SHA1, SHA256, MD5, humanhash, imphash, ssdeep, TLSH), URLs, IP addrs, domains, other IOCs

ImportHash.ps1 (in progress):
- Creates a hash based on imported library names, see https://www.mandiant.com/resources/blog/tracking-malware-import-hashing

ImportHash.ps1 notes:
* Grab [Get-PE1.py](https://github.com/mattifestation/PowerShellArsenal/blob/master/Parsers/Get-PE.ps1), [MemoryTools.ps1](https://github.com/mattifestation/PowerShellArsenal/blob/master/MemoryTools/MemoryTools.ps1), [Get-SystemInfo.ps1](https://github.com/mattifestation/PowerShellArsenal/blob/master/WindowsInternals/Get-SystemInfo.ps1), [PS-Reflect.psm1](https://github.com/mattifestation/PowerShellArsenal/blob/master/Lib/PSReflect/PSReflect.psm1), then place them in the same directory as the script.
* Include the following dot-sourcing and module import lines at the head of Get-PE1.py:
~~~
. .\Get-SystemInfo.ps1
. .\MemoryTools.ps1
Import-Module .\PSReflect.psm1
~~~
* Thanks to @mattifestation for writing the PowerShell PE parser, Get-PE.ps1, and related tools

Example use:
~~~
$importHash = Get-ImpHash -path ".\notepad.exe"
Write-Output $importHash
~~~

ImportHash.ps1 future work:
* The ordinal lookup function needs additional testing
* This script has yet to be refactored according to this [style guide](https://github.com/mattifestation/PowerShellArsenal/tree/master#script-style-guide)
