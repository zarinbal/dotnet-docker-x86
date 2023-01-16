# escape=`

FROM mcr.microsoft.com/windows/servercore:ltsc2019

ENV `
    # Configure web servers to bind to port 80 when present
    ASPNETCORE_URLS=http://+:80 `
    # Enable detection of running in a container
    DOTNET_RUNNING_IN_CONTAINER=true `
    # .NET Runtime version
    DOTNET_VERSION=6.0.13

# Install .NET Runtime
RUN powershell -Command `
        $ErrorActionPreference = 'Stop'; `
        $ProgressPreference = 'SilentlyContinue'; `
        `
        Invoke-WebRequest -OutFile dotnet.zip https://dotnetcli.azureedge.net/dotnet/Runtime/$Env:DOTNET_VERSION/dotnet-runtime-$Env:DOTNET_VERSION-win-x86.zip; `
        $dotnet_sha512 = '8B36B4EE8F1ABE4BE6E48F7D17A815EF4A7C591FEF8D5CEC2E8D33905CEFA91F5F14448F7E33393C8C2268782F255CCD6A6B6EB10A7D69EFA986095AE862B3EF'; `
        if ((Get-FileHash dotnet.zip -Algorithm sha512).Hash -ne $dotnet_sha512) { `
            Write-Host 'CHECKSUM VERIFICATION FAILED!'; `
            exit 1; `
        }; `
        `
        mkdir ${env:ProgramFiles(x86)}\dotnet; `
        tar -oxzf dotnet.zip -C ${env:ProgramFiles(x86)}\dotnet; `
        Remove-Item -Force dotnet.zip

RUN setx /M PATH "%PATH%;C:\Program Files (x86)\dotnet"
