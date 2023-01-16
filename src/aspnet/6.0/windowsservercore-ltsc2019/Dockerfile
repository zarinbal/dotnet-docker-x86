# escape=`

ARG REPO=zarinbal/dotnet-x86-runtime
FROM $REPO:6.0.13-windowsservercore-ltsc2019

# ASP.NET Core version
ENV ASPNET_VERSION=6.0.13

# Install ASP.NET Core Runtime
RUN powershell -Command `
        $ErrorActionPreference = 'Stop'; `
        $ProgressPreference = 'SilentlyContinue'; `
        `
        Invoke-WebRequest -OutFile aspnetcore.zip https://dotnetcli.azureedge.net/dotnet/aspnetcore/Runtime/$Env:ASPNET_VERSION/aspnetcore-runtime-$Env:ASPNET_VERSION-win-x86.zip; `
        $aspnetcore_sha512 = 'A72345B4612C342D8A3CDB037D90799E00F9C6C5B2A3DD35300D187FE9BACCD016D0651E414B2CF9D99BFDB3FAF6A69D04F6AFEE94E3F4D4F0CFB18040916B9B'; `
        if ((Get-FileHash aspnetcore.zip -Algorithm sha512).Hash -ne $aspnetcore_sha512) { `
            Write-Host 'CHECKSUM VERIFICATION FAILED!'; `
            exit 1; `
        }; `
        `
        tar -oxzf aspnetcore.zip -C ${env:ProgramFiles(x86)}\dotnet ./shared/Microsoft.AspNetCore.App; `
        Remove-Item -Force aspnetcore.zip; 
