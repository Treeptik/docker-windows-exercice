# escape=`
FROM microsoft/windowsservercore  
SHELL ["powershell", "-Command", "$ErrorActionPreference = 'Stop';"]

RUN Install-WindowsFeature Web-Server
RUN Remove-Item C:\inetpub\wwwroot\*.*

ENTRYPOINT ["C:\\ServiceMonitor.exe", "w3svc"]