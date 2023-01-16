# dotnet-docker-x86
This is a x86 implementation of x86 dotnet framework for windows containers. This covers the version LTS Runtime, ASP.NET, and the SDK version.


## Usage:
```
docker run -it zarinbal/dotnet-x86-runtime cmd.exe
```
```
docker run -it zarinbal/dotnet-x86-aspnet cmd.exe
```
```
docker run -it zarinbal/dotnet-x86-sdk cmd.exe
```


## Build:

### Runtime:


```
docker build .\src\runtime\6.0\windowsservercore-ltsc2019 -t zarinbal/dotnet-x86-runtime  -t zarinbal/dotnet-x86-runtime:6.0.13 -t zarinbal/dotnet-x86-runtime:6.0.13-windowsservercore-ltsc2019 -t zarinbal/dotnet-x86-runtime:6.0
```


### Aspnet
```
docker build .\src\aspnet\6.0\windowsservercore-ltsc2019 -t zarinbal/dotnet-x86-aspnet  -t zarinbal/dotnet-x86-aspnet:6.0.13 -t zarinbal/dotnet-x86-aspnet:6.0.13-windowsservercore-ltsc2019 -t zarinbal/dotnet-x86-aspnet:6.0
```
### Sdk
```
docker build .\src\sdk\6.0\windowsservercore-ltsc2019 -t zarinbal/dotnet-x86-sdk  -t zarinbal/dotnet-x86-sdk:6.0.13 -t zarinbal/dotnet-x86-sdk:6.0.13-windowsservercore-ltsc2019 -t zarinbal/dotnet-x86-sdk:6.0
```

## Pushing to docker hub:
```
docker push zarinbal/dotnet-x86-runtime --all-tags
docker push zarinbal/dotnet-x86-aspnet --all-tags
docker push zarinbal/dotnet-x86-sdk --all-tags
```


