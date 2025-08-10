Open PowerShell as Administrator (right-click → Run as Administrator).

Create the block rule:

powershell
New-NetFirewallRule -DisplayName "Block Telnet 23" -Direction Inbound -Protocol TCP -LocalPort 23 -Action Block -Enabled True -Profile Any
Get your active IPv4 addresses (pick the adapter IP you’ll test from):

powershell
Get-NetIPAddress -AddressFamily IPv4 | Where-Object {$_.IPAddress -notlike "127.*"} | Select-Object IPAddress
Test the block (replace <IP> with the chosen adapter IP, e.g. 192.168.48.1):

powershell
Test-NetConnection -ComputerName <IP> -Port 23
Remove the test rule:

powershell
Remove-NetFirewallRule -DisplayName "Block Telnet 23"
Confirm the rule is gone (no output expected):

powershell
Get-NetFirewallRule -DisplayName "Block Telnet 23"