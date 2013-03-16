This Old Video Site: How PBS streams video
===========================

**Presenter:** Edgar Roman

**Track:** II

**Description:**

Overview of how the Public Broadcasting Service streams video online. Learn how PBS uses python and other services to provide video streaming online. Talk will discuss lessons learned, explanation of video formats, and experiences with mobile device support. Talk will include recommendations for others to easily adopt similar practices to quickly host their own online video site.

    https://us.pycon.org/2013/schedule/presentation/133/

Goals
+++++

PBS wants to be as accessible as possible, which means supporting as many
devices as possible.

H.264 is widely supported, but it lives under a legal cloud.

They want to play ads and have flexibility to support social sharing.

Delivery
+++++

You can use HTTP, but they use RTMP at PBS.

In 2009 the standard was 400kbps, but now it's more like 800kbps to 1.2mpbs

Targets Devices
+++++

* Apple's iOS
    * No Flash
    * Http Live Streaming (HLS)
    * Auto bitrate adjust possible
    * Any CDN will do
    * Built-in player
* Android
    * So many variants that it's difficult to determine what the device will
      support
    * Later versions support HLS
    * End up using MP4 baseline

HTML5 Video Tag
+++++

Great for supported devices, but doesn't support the rich environment features
that they need, especially advertising and captioning.

There are some really good frameworks:

* VideoJS
* MediaElement
* JWPlayer

Transcoding
+++++

Local:

* ffmpeg
* x264
  Handbrake

Online:

* Zencoder
* Encoding.com

They create 16 streams for each video, but they start wth 5 Mbps

Stealing
+++++

PBS offers free streaming lonline to there is less motivation to steal.

Beware of the DRM Graveyard
