# escape=`
FROM microsoft/windowsservercore
SHELL ["powershell", "-Command", "$ErrorActionPreference = 'Stop';"]

EXPOSE 80 443
ENV NGINX_VERSION 1.13.9

RUN Invoke-WebRequest -Uri ""http://nginx.org/download/nginx-$($env:NGINX_VERSION).zip" -OutFile "nginx.zip"; `
    Expand-Archive -LiteralPath C:\nginx.zip -DestinationPath C:\; `
    Rename-Item "nginx-$($env:NGINX_VERSION)" nginx; `	
	Remove-Item nginx.zip -Force
	Remove-Item C:\nginx\html\*.*

WORKDIR c:/nginx
COPY nginx.conf ./conf/
CMD .\nginx