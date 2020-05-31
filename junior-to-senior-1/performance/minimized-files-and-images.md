---
description: Honey I shrink the files
---

# Minimized Files and Images

**Minimized Files**

Build process when an app is ready for production using Webpack to minimize HTML, CSS and JS files. Because machine does not care about indentation or white-spaces, so we eliminates these to get more optimized files.

**Minimized Images**

Know the difference between JPG, PNG, GIF and SVG and their specific usage.

Rules of thumbs:

1. If you want transparency: use a PNG
2. If you want animations where colour is not issue: use a GIF
3. If you want colourful images: use a JPG
4. If you want a simple icons, logos and illustrations: use a SVG. Can be expanded beyond its original size and still look sharp
5. Reduce PNG with TinyPNG website
6. Reduce JPG with JPEG-optimizer
7. Try to choose simple illustrations over highly detailed photographs where applicable
8. Always lower JPG image quality \(30-60%\) before saving the files
9. Resize image based on size it will be displayed
10. Display different sized images for different background. \(i.e. media queries CSS, but downsides is you need to save different files in different sizes for different devices\)
11. Use CDN like imigx. Uploading all the images into an optimized external server.
12. Remove image metadata \(good for security as well to remove unnecessary info about the photo - like device to take the picture and the location of the image\)



