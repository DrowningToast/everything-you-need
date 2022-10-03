# everything-you-need

**Now we are in hacktoberfest event month so I'm very happy to publish this publicly for you guys to share your computer graphics idea or your sample app that can be video, github repo, or push source code directly to this repo**

**I need your idea to make it happended and break my computer graphics knowledge.**

## Idea List

---

### Idea 001 by [LordBenz](https://github.com/lordbenz)

It would be great if we have some tool that can auto-generate outfit styles that match with user's brand logo. By the way, we can start from simple thing like picking color from logo, adding them to color picker like Canva did (image attached).
![](/images/canva-logo-color-feat.png)

- In web development we can just use somethings like

  `const ctx = canvas.getContext("2d");`

  Then, use `ctx.getImageData(0, 0, canvas.width, canvas.height)` for getting the image pixels.
  With those pixels, we can re- arrange to the new palette of color that we want.

  After we can do this success, we can think about how to auto generate style from these color palettes.

---
