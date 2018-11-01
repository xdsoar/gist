#Download the latest OpenSSH for Windows binaries (package OpenSSH-Win64.zip or OpenSSH-Win32.zip)
#As the Administrator, extract the package to C:\Program Files\OpenSSH
#As the Administrator, install sshd and ssh-agent services: 
powershell.exe -ExecutionPolicy Bypass -File install-sshd.ps1


#Allow incoming connections to SSH server in Windows Firewall:
#Either run the following PowerShell command (Windows 8 and 2012 or newer only), as the Administrator: 

New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH SSH Server' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22

#or go to Control Panel > System and Security > Windows Firewall1 > Advanced Settings > Inbound Rules and add a new rule for port 22.

Start the service and/or configure automatic start:
Go to Control Panel > System and Security > Administrative Tools and open Services. Locate OpenSSH SSH Server service.
If you want the server to start automatically when your machine is started: Go to Action > Properties. In the Properties dialog, change Startup type to Automatic and confirm.
Start the OpenSSH SSH Server service by clicking the Start the service.
