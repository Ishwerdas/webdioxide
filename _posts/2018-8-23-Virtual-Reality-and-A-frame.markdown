---
published: true
layout: post
date: '2016-8-23 00:08:19 +0530'
categories: links
author: Shaina Sabarwal
image: notes.jpg
permalink: /vr/virtual-reality-and-aframe.html
comments: true
title: Virtual Reality Arriving Fast
---

- Microsoft Hololens experience showcase opens for developers in New York.
- Facebook is hiring a News and Media Content Lead for Oculus Rift.
- A GearVR puzzle game E2per Review by VRift
- Google reveals the plans for new VR headset and motion controller.
- The WaveVR raises $2.5 million to mix music and virtual reality


If you have ever heard such news, you would be wondering that every big company is stepping into 3-Dimensional VR interfaces. They are making hardware like head sets, apps, platforms to develop apps, having conferences, funding, and a lot.

#### So, first let's learn, what is this all hype about? What is that we call Virtual Reality?

**Virtual Reality** is a computer technology that simulates user's presence and environment for interactions that includes, sight, touch, hearing and smell, to create a lifelike experience.

#### How is it evolved?

Remember that red and green glasses we used to see 3D images in our childhood? Those are known as **Anaglyph 3D glasses** which were used to create stereoscopic 3D effect. When views through the color-coded anaglyph glasses, each of the two differently filtered colored images reaches the eye it's intended for, revealing a 3D image in front of your eyes.

![Anaglyph 3D Glasses]({{ site.url }}/images/colored3d.jpg)

After Anaglyph glasses, polarized 3D glasses came into use, to watch 3D animated movies or 3D games. In polarized 3D system, two images are projected superimposed onto the same screen and polarization glasses are used to create the illusion of 3D images.

![Polarized 3D Glasses]({{ site.url }}/images/fluidglasses.jpg)

Now, to have a super interactive virtual reality experience, companies are making interfaces like Oculus Rift, Samsung GearVR etc, but these are not so affordable yet.
Google has also made a low level alternative to Oculus Rift at very affordable rate, known as Google Cardboard, so that everyone can experience VR today.

![Google Cardboard]({{ site.url }}/images/googlecardboard.jpg)

#### How we see things in 3D around us in real world?

As our eyes sit side by side, each eye captures a slightly different view of an object. This is called binocular vision. When signals from the two eyes reach the brain, they are superimposed and processed into a single picture with depth. As a result, we get a 3D picture and are able to judge distances well.

This is the concept from where the virtual reality get inspired from.  
Developers of VR apps make two different images or models of same object placed at angles that are slightly different from each other, one for each eye. Then we have to use a VR hardware like Google Cardboard or Oculus Rift to have 3D view of that image or model.

From all this above, we come to know that the next interface that is approaching fast is VR interfaces. Developers will be in need to make the sites and apps responsive for these interfaces too, as today they do for mobiles and tablets.

So to have a good taste of developing VR apps, I used A-frame. 

#### What is A-frame?

A-frame is an open-source framework for creating 3D and virtual reality experiences on the web. It's like the bread to your sandwich, which will provide you with some ready made entities that you can use to make interesting applications. VR scenes created by A-frame work across desktop, oculus rift, mobiles, Google cardboard with just HTML.

A-frame is powered by three.js and WebVR. Three.js is a javascript library that is used to create 3D scenes and WebVR is another javascript API that provides access to the VR devices such as Oculus Rift, Google Cardboard etc.

To make a 3D scene in a-frame, you just need to make an HTML file, add a-frame script in the <head> and add entities you want in the <body>.

```
<html>
<head>
<script src="aframe.js"></script>
</head>
<body>
<a-scene>
  <a-box position="0 1 0" height="1" width="1"></a-box>
</a-scene>
</body>
</html>
```

