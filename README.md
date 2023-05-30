## Prerequisite

1. Download and install [.NET SDK](https://dotnet.microsoft.com/en-us/download)
2. Have a game [instrumented with AltTester Unity SDK](https://alttester.com/docs/sdk/pages/get-started.html#instrument-your-game-with-alttester-unity-sdk)
3. Have [AltTester Desktop app](https://alttester.com/alttester/) installed (to be able to inspect game)
4. Download and install iProxy (for [Windows there are binaries builded here](https://github.com/L1ghtmann/libimobiledevice/releases), while for MacOS and Linux there are official install steps on [libimobiledevice](https://libimobiledevice.org/#get-started))
    - On Windows just add path of the exe files to environment system PATh variable in order to be available from everywhere (as AltDriver command implements that)

# Tests created with NUnit & AltTester-Driver for a game developed w/ Unity (TrashCat)

This repository is a test project that uses NUnit as the test library. It was generated using following command (as suggested in [documentation](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-with-nunit#creating-the-test-project))

```
dotnet new nunit
```

[AltTester Unity SDK framework](https://alttester.com/docs/sdk/) contains `AltDriver` class used to connect to the instrumented game developed w/ Unity. AltTester-Driver for C# is available as a nuget package. Install [AltTester-Driver nuget package](https://www.nuget.org/packages/AltTester-Driver#versions-body-tab)

```
dotnet add package AltTester-Driver --version 1.8.2
```

# Setup for running on mobile device

1. Install the app on device
    - only **from macOS, using Xcode** could install app as .ipa file
    - depending on macOS version, [corresponding Xcode version had to be installed](https://developer.apple.com/support/xcode/)

2. Check device is connected via USB and can it be accessed, execute:

```
idevice_id
```

or

```
ideviceinfo
```

# Run tests manually (with [dotnet CLI](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-test))

1. Launch game manually
2. From `TrashCatTests` execute all tests:

```
dotnet test
```

! **Make sure to have the AltTester Desktop App closed, otherwise the test won't be able to connect to proper port.**

### Run all tests from a specific class / file

```
dotnet test --filter <test_class_name>
```

### Run only one test from a class

```
dotnet test --filter <test_class_name>.<test_name>
```

### Workaround for being able to use SDK 1.8.2 installed as package in project:
- get `altwebsocket-sharp.dll` from [here](https://github.com/alttester/AltTester-Unity-SDK/tree/development/Assets/AltTester/Runtime/3rdParty/websocket-sharp/netstandard2.0) and put in project's bin\Debug\net7.0