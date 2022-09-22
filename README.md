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

- Unity 2019.4

On Unity 2021.1 or earlier versions, KlakNDI requires the [.NET Standard 2.0]
profile -- You can't compile the package with the .NET 4.x profile.

[.NET Standard 2.0]:
  https://docs.unity3d.com/2020.1/Documentation/Manual/dotnetProfileSupport.html

From Unity 2021.2, KlakNDI is compatible with both the .NET Standard and .NET
Framework profiles.

Desktop platforms:

- Windows: x64, D3D11/D3D12
- macOS: x64 or arm64 (M1), Metal

Known Issues and Limitations
----------------------------
- Dimensions of frame images should be multiples of 16x8. This limitation causes
  glitches on several mobile devices when using the Game View capture method.
  
  - When using NDI mode, it doesn't support audio streaming. There are several technical
difficulties to implement without perceptible noise or delay, so there is no
plan to implement it.

How To Install
-------------------
As mentioned above, this package requires Klak Spout and Klak NDI]


