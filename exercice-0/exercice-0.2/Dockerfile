# escape=`
FROM microsoft/windowsservercore

RUN powershell -Command `

  # Télécharger les logiciels ; `

  wget https://www.apachelounge.com/download/VC11/binaries/httpd-2.4.18-win32-VC11.zip -OutFile c:\apache.zip ; `
  wget "https://download.microsoft.com/download/1/6/B/16B06F60-3B20-4FF2-B699-5E9B7962F9AE/VSU_4/vcredist_x86.exe" -OutFile c:\vcredist.exe ; `
  wget -Uri http://windows.php.net/downloads/releases/php-5.5.33-Win32-VC11-x86.zip -OutFile c:\php.zip ; `

  # Installer les logiciels ; `

  Expand-Archive -Path c:\php.zip -DestinationPath c:\php ; `
  Expand-Archive -Path c:\apache.zip -DestinationPath c:\ ; `
  start-Process c:\vcredist.exe -ArgumentList '/quiet' -Wait ; `

  # Supprimer les fichiers non nécessaires ; `

  Remove-Item c:\apache.zip -Force; `
  Remove-Item c:\vcredist.exe -Force; `
  Remove-Item c:\php.zip