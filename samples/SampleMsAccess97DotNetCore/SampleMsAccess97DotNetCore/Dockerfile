#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

#Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
#For more information, please see https://aka.ms/containercompat

FROM zarinbal/dotnet-x86-aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM zarinbal/dotnet-x86-sdk:6.0 AS build
WORKDIR /src
COPY ["SampleMsAccess97DotNetCore/SampleMsAccess97DotNetCore.csproj", "SampleMsAccess97DotNetCore/"]
RUN dotnet restore "SampleMsAccess97DotNetCore/SampleMsAccess97DotNetCore.csproj"  --runtime win-x86
COPY . .
WORKDIR "/src/SampleMsAccess97DotNetCore"
RUN dotnet build "SampleMsAccess97DotNetCore.csproj" -c Release -o /app/build --runtime win-x86 --self-contained

FROM build AS publish
RUN dotnet publish "SampleMsAccess97DotNetCore.csproj" -c Release -o /app/publish --self-contained --runtime win-x86

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "SampleMsAccess97DotNetCore.dll", "-r win-x86"]