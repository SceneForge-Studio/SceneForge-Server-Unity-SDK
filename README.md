# SceneForge Server Unity SDK
**SceneForge Server SDK** is a Unity Plugin that allows for sending and receiving video streams and tracking data in and out of SceneForge Server.
It makes use of [Spout] (Windows Only) and [NDI]®.  You can choose one or the other before entering play mode.

**Note:** Only NDI can carry tracking metadata, and the system requires the editor (or build) to be in Play Mode in order to use it.

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

Simply attach the **SceneForge Server** component to any object in your scene.
You can have multiple **SceneForge Server** components in your scene that operate independently of each other, but ensure that they are each on their own GameObject.

![image](https://user-images.githubusercontent.com/40009793/191862257-a8b38e76-e324-413d-a7de-1f7ad77e107f.png)

- **Source Type**: You can select a source type:  NDI or Spout.
- **Source Name**: You can enter an input source name, or choose from a list of detected sources.
- **Target Renderer**:  You can choose a target mesh renderer to output the source.
- - When a target renderer is specified, you can enter a shader property to override.  By default, this value is set to `_MainTex`, but you may need to change it depending on the desired effect and shader.
- **Tracking Type**:  This allows you to choose what type of tracking you will be using.  This section is only shown if you are using NDI.
- - You can choose between `None`, `Body`, or `Mobile`.
- - - `Body` Requires your transform to be set up in a certain way, while `Mobile` will move the desired transform by the recieved translation.  More info about tracking is below.

Tracking
-----------
As mentioned above, when using NDI, you can choose between either disabling recieved tracking, reading Body tracking data, or Mobile tracking data.

When the mode is enabled, you must specify a target transform to apply the tracking to.

### Body
This is the local position and rotation of a child transform within an empty parent.  This child will act as the "object" that the chromakey footage is projected on, and it will move according to the tracked person from the SceneForge Server application.  

### Mobile
This will move the target transform by the recieved tracking data, starting at the object's starting position.  So set up your target transform at the desired starting position before playing, then when tracking data is recieved, translation and rotation will occur with each recieved frame.

Recording
-----------
You can use the Unity Recorder or Timeline package to record the recieved tracking data for future playback.  This is useful for recording multiple takes.


What's the difference between NDI and Spout?
------------------------------
- NDI: Video-over-IP codec/protocol
- Spout: Interprocess GPU memory sharing on DirectX

NDI requires CPU/memory/network load, but it's greatly versatile.

Spout doesn't produce any CPU load, but its range of application is limited.

If you're trying to share videos between applications running on a single
Windows PC, Spout would be a better solution.

But, if you want access to tracking data, at this time NDI is the only option that supports additonal metadata.  More options will come in the future.
