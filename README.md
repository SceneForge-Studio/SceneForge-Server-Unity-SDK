# SceneForge Server Unity SDK
**SceneForge Server SDK** is a Unity Plugin that allows for sending and receiving video streams and tracking data in and out of SceneForge Server.
It makes use of [Spout] (Windows Only) and [NDI]®.  You can choose one or the other before entering play mode.

**Note:** Only NDI can carry tracking metadata.

[Spout]: http://spout.zeal.co/

[NDI]: https://www.ndi.tv/
[NewTek]: https://www.newtek.com/

Components
-------------------
The SceneForge Server SDK makes use of [Klak Spout] and [Klak NDI] for video streaming, and acts as a wrapper to make the process more streamlined.
It also handles reading and using tracking data for you.
For notes on installation, see below.

[Klak NDI]: https://github.com/keijiro/KlakNDI
[Klak Spout]: https://github.com/keijiro/KlakSpout


System Requirements
-------------------
Spout only works on Windows PCs
- Unity 2020.3 or Later

**NDI**

On Unity 2021.1 or earlier versions, NDI requires the [.NET Standard 2.0]
profile -- You can't compile the package with the .NET 4.x profile.

[.NET Standard 2.0]:
  https://docs.unity3d.com/2020.1/Documentation/Manual/dotnetProfileSupport.html

From Unity 2021.2, NDI is compatible with both the .NET Standard and .NET
Framework profiles.

**Spout**

Windows System with DirectX 11/12 support.

Desktop platforms:

- Windows: x64, D3D11/D3D12
- macOS: x64 or arm64 (M1), Metal

Installation
---------------
Before downloading this package, make sure that Klak NDI and Klak Spout are Installed.
On MacOS, Klak Spout is not required.

Follow the installation instructions in each of the packages below.

https://github.com/keijiro/KlakNDI
https://github.com/keijiro/KlakSpout

Known issues and limitations from those packages are present in this one, but won't be a problem for SceneForge usage.

**Then, once that is set up, you can download and install this package.**

Usage
-----------
You can use each of the above packages individually with no trouble, but the SceneForge component provides a more streamlined solution.  Additionally, using the original Klak NDI plugin won't support tracking data from SceneForge Server.

Simply attach the **SceneForge Server Manager** component to any object in your scene.






What's the difference between NDI and Spout?
------------------------------
- NDI: Video-over-IP codec/protocol
- Spout: Interprocess GPU memory sharing on DirectX

NDI requires CPU/memory/network load, but it's greatly versatile.

Spout doesn't produce any CPU load, but its range of application is limited.

If you're trying to share videos between applications running on a single
Windows PC, Spout would be a better solution.

But, if you want access to tracking data, at this time NDI is the only option.  More will come in the future.
