# .NET Core on Raspberry Pi

Arm32 support for .NET Core is still being brought up but there are now daily runtime builds that are ready to use. 
There is no SDK that runs on ARM32 yet but you can publish an application that will from on a Raspberry Pi. 

These steps have been tested on both a Pi 2 and Pi 3 on Linux and Windows with success.

##Creating an app:

* [Install .NET Core 2.0 SDK](https://github.com/dotnet/cli/tree/master) into a supported developer configuration.

* From the terminal/commandline create a folder named helloworld and go into it.
* Run `dotnet new`.
* Edit the helloworld.csproj file to look like this (Note the version may be newer under RuntimeIdentifiers).

```
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
    <RuntimeFrameworkVersion>2.0.0-beta-001509-00</RuntimeFrameworkVersion>
    <RuntimeIdentifiers>win8-arm</RuntimeIdentifiers>
  </PropertyGroup>

</Project>
```

* Run `dotnet restore`.

* Run `dotnet publish` to publish the application for arm.

* Under `./bin/Debug/netcoreapp2.0/win8-arm/publish` or `.\bin\Debug\netcoreapp1.1\publish` you will see the whole self contained app that you need to copy to your Raspberry Pi.


##Getting the app to run on the Pi.

###Linux (Ubuntu)

* Install [Ubuntu 14.04 or 16.04](https://www.raspberrypi.org/downloads/) on your Pi.

* Install the [prereq packages](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) for .NET Core. 

* Copy your app to the Raspberry Pi and execute run `./helloworld.exe` to see `Hello World!` from .NET Core running on your Pi!

Note: While it is possible to build the product on the Pi, it isn't easy today and it's slow. We are working on making it very easy to do.

###Win10 IoT Core

* Install [Windows 10 IoT Core](https://developer.microsoft.com/en-us/windows/iot/GetStarted) on your Pi.

* Copy your app to the Raspberry Pi and execute run `helloworld.exe` to see `Hello World!` from .NET Core running on your Pi!

* `helloworld.dll` and you should see `Hello World!` from .NET Core running on your Pi!