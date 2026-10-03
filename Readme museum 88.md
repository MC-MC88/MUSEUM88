<div align="center">

🖼️ Museum 88

A gallery that treats images like artifacts, not content.

</div>

---

👋 Welcome

Every image gallery I've used online felt like a warehouse. A grid of thumbnails, infinite scroll, no sense of where you are or what you've seen. Pinterest, Unsplash, even the photo app on my phone — they all treat images as things to be consumed, in bulk, as fast as possible.

Museum 88 treats images the way a museum does. One at a time. In the center. With everything else dimmed, waiting, and quiet.

It's a horizontal gallery. A row of images that scrolls side to side, with the one in the middle standing out — full color, full brightness, slightly larger than the rest. The ones to the left and right are grayscale, dimmed, and rotated a few degrees away from you. Peripheral vision. Things you're walking past. Things you'll get to.

The effect is subtle, but it changes how you look. In a grid, your eyes dart between twelve images at once and land on nothing. Here, there's only ever one image that's fully alive. You look at it. You scroll. You look at the next one. It's slower, and that slowness is the whole point.

The design leans architectural. A blackletter font for the title — UnifrakturMaguntia, the kind of type you'd find on a museum's letterhead from 1900. Everything else in Inter, thin weights, generous spacing. Cards are tall, rounded, spaced far apart. A thin line at the top of the page shows how far you've come. At the bottom, a floating pill with three circular buttons — previous, random, next. A moon in the corner for the light theme.

The images aren't in the file. You drop them in. One hundred and twenty numbered slots, ready for whatever you want to put there.

---

<!--
## 📸 Look Inside

<br />

<div align="center">
  <img src="https://github.com/mohamed005cheikh-rgb/museum88/raw/main/images/preview-1.png" alt="The gallery in dark mode" width="100%" />
  <br />
  <sub><b>① Dark mode — the default</b></sub>
</div>

<br />
<br />

<div align="center">
  <img src="https://github.com/mohamed005cheikh-rgb/museum88/raw/main/images/preview-2.png" alt="The gallery in light mode" width="100%" />
  <br />
  <sub><b>② Light mode — the toggle in the corner</b></sub>
</div>

<br />
<br />

<div align="center">
  <img src="https://github.com/mohamed005cheikh-rgb/museum88/raw/main/images/preview-3.png" alt="A single artifact centered" width="100%" />
  <br />
  <sub><b>③ One image alive at a time</b></sub>
</div>
-->

---

✨ What you'll find

A horizontal walk, not a vertical scroll.
The gallery runs left to right, not top to bottom. Each card takes up most of the screen, so there's only room for one and a bit at a time. You don't scan — you move. The scroll snap makes sure you always land cleanly on one image, never halfway between two.

One image alive at a time.
Each card has two states: peripheral and active. Peripheral cards are grayscale, dimmed to 70% brightness, scaled to 92%, and rotated 8 degrees away from you. Active cards are full color, full brightness, straight-on, and slightly larger. An IntersectionObserver decides which is which, based on which card is closest to the center of the viewport. Only one card is ever in the "active" state. Everything else is context.

A 3D rotation on every card.
Cards use CSS transform: rotateY(-8deg) scale(0.92) with a perspective: 1200px on the container. The effect is like standing in a long gallery and looking down the row — everything to the sides is angled away from you. When a card slides to the center, it rotates flat and comes into focus. The transition takes 0.8 seconds on a cubic-bezier(0.16, 1, 0.3, 1) curve — the same easing Apple uses for its spring animations. It feels physical, not digital.

Two themes, dark by default.
The default is black-on-dark: #050505 background, #ededed text, #111111 cards. Everything reads as one continuous surface, like a dark gallery with hidden lighting. The circular button in the bottom-right corner toggles to a light theme — #f5f5f7 background, #111111 text, white cards. Both themes transition over 0.6 seconds, so the switch feels like the lights coming up rather than a page reload.

A progress bar that tells you where you are.
A thin line at the very top of the page, three pixels high, that fills from left to right as you scroll. It's not a scrollbar — it's a sense of place. At zero, you're at the beginning. At full, you're at the end. On a gallery with a hundred images, that line is the only way to know how far you've come.

Four ways to move.
Scroll with your mouse or trackpad. Swipe on a touchscreen. Click the previous and next buttons. Press the left and right arrow keys. All four are always available, and all four do the same thing: they center the next or previous image. There's no mode to switch, no setting to configure. Pick whichever feels natural and go.

A random jump, for when you don't know what you want.
The middle button in the floating control pill is a randomiser. It picks one of the 120 images at random and scrolls to it, smoothly, in one motion. It's useful when you've already seen the first ten and want to see something from the back. It's also useful when the gallery is long enough that scrolling to the end feels like work.

Lazy loading, so 120 images don't kill your browser.
Every <img> element uses loading="lazy", which means the browser only fetches images as they come close to the viewport. On a gallery with a hundred and twenty high-resolution photos, this is the difference between a page that opens in a second and a page that doesn't open at all. You can put full-size images in the folder and the browser will figure out how much to load and when.

A blackletter title, quietly fixed.
UnifrakturMaguntia at the top-left, rendered at 2.5rem, sitting still while the gallery scrolls behind it. It's not animated, not styled with effects, not trying to be a hero. It's the letterhead. It tells you where you are, and then it gets out of the way.

A mask that fades the edges.
The gallery container has a CSS mask — linear-gradient(to right, transparent, black 15%, black 85%, transparent). This makes the cards fade to nothing at the far left and far right edges of the screen, instead of being clipped off mid-image. It's a small thing, but it makes the gallery feel like it extends beyond the screen in both directions, like a wall that keeps going.

Drop the folder, it works.
The gallery expects images at pictures/1.jpg through pictures/120.jpg. Drop your images in a folder with that name, put the HTML file next to it, and the gallery populates itself. No config file, no JSON, no build step, no backend. Everything is generated in JavaScript on page load.

---

🧭 How it works

1. Get the HTML file.
One file. That's the whole program. Double-click it and it opens in your browser.

2. Drop your images in a pictures folder.
The gallery looks for pictures/1.jpg, pictures/2.jpg, pictures/3.jpg, and so on, up to pictures/120.jpg. Any image format that ends in .jpg works. Any size works — they'll be cropped to fit the card. If you have fewer than 120, the empty slots just won't load. If you have more, only the first 120 will appear.

3. Open the file.
The first image loads in the center. The ones to the left and right sit in their peripheral state — grayscale, dimmed, angled away.

4. Move through the gallery.
Scroll with your trackpad or mouse. Swipe on a touchscreen. Click the arrow buttons at the bottom. Press the left and right arrow keys. Or click the middle button and let it choose for you.

5. Watch a card come alive.
As a card slides toward the center, it rotates flat, brightens, and gains color. When it reaches the middle, it's the only thing in the room. When you move past it, it goes back to being peripheral.

6. Flip the lights, if you want.
The circular button in the bottom-right corner switches between dark and light. Your choice isn't saved — every visit starts dark, because that's the mood the gallery was built for.

7. Close the tab.
No account, no state, no history. The next time you open the file, you start at the first image again.

---

🛠️ A few small helps

"Where do I put my images?"
In a folder named pictures, next to the HTML file. The images should be named 1.jpg, 2.jpg, 3.jpg, and so on. The gallery will find them automatically. If you want to use .png or .webp instead, open the HTML file in a text editor and change the .jpg at the end of pictures/${i}.jpg to your format.

"How many images can I have?"
As many as you want, but the default is 120. The number is set in one place — const totalImages = 120; near the top of the script. Change the number to anything you want. A hundred and twenty is a good default: enough to feel like a collection, small enough that the browser stays fast.

"Only some of my images are loading."
That's loading="lazy" doing its job. The browser only fetches images as they come close to the viewport. This is what keeps a gallery with a hundred and twenty high-resolution photos from freezing on open. If you want all images to load at once — for a presentation, or on a fast local machine — open the file and remove the img.loading = 'lazy'; line near the top of the script. But expect the page to take longer to open.

"Some of my images are huge and the page is slow."
Resize them before you put them in the folder. A gallery card is roughly 700 pixels wide, so images larger than 1400 pixels on the long edge are wasted bytes. Anything under 500 KB per image will feel instant. Anything over 5 MB will make the browser stutter as it scrolls.

"Does it work on a phone?"
Yes. Swipe to scroll, and the control buttons at the bottom work with taps. The card size and spacing adjust for smaller screens. The layout is designed for a phone first — that's where I built it — and scales up to a desktop without anything breaking.

"The active card doesn't update when I scroll."
That usually means the IntersectionObserver isn't firing. The most common cause: you opened the HTML file directly from your filesystem (file://), and your browser is being strict about how the observer's root is calculated. Serve the file from a local web server — anything from Python's http.server to a static host — and it works perfectly.

"Can I change the theme permanently?"
Yes. Open the file and add the class light to the <body> element — the whole gallery starts in light mode. To make dark the only option, remove the theme-toggle button from the HTML entirely. To remove the toggle but keep both themes available, leave the button in but hide it with display: none in CSS.

"Why does the gallery start at image 1 every time?"
Because nothing is saved. The gallery has no memory — no localStorage, no cookies, no session. Every time you open the file, you start at the beginning. This is deliberate: the gallery is meant to be opened, walked through, and closed. It's not a browser, and it's not supposed to remember what you looked at.

"Does it work offline?"
Almost. The gallery runs entirely in your browser and never makes a network request to anything except the Google Fonts CDN, where it fetches UnifrakturMaguntia and Inter. Load the page once with network, and the fonts are cached. After that, it works offline. If you want it fully self-contained, download the two font files and change the <link> tags to point at them locally.

"Can I link directly to image 47?"
Not as written. The gallery doesn't use URL fragments — there's no way to jump to a specific image from outside the page. If you want this, you'd need to add URL hash handling: read window.location.hash on load, and if it matches #47, scroll to the 47th card. It's a small change to the init code, but it's not built in.

"What's with the blackletter title?"
UnifrakturMaguntia is a real blackletter typeface, based on a type cut by Johann Zainer around 1470. It's the font you'd find on German books printed before 1940, and it's the visual signal that says "this is old, this is curated, this is a place where things are kept." In a gallery that treats images as artifacts, it's the right register.

"Why does the top progress bar go all the way across on the last image but not the first?"
The bar is a percentage of your current scroll position. At the very start, it's zero. At the very end, it's one hundred percent. The math is scrollLeft / (scrollWidth - clientWidth), which is the standard formula for scroll progress. There's a small amount of tension between "start" and "end" because the first and last cards can't be exactly centered — they're at the ends of the scroll track. The bar handles that gracefully.

"Can I add titles or captions to the images?"
Not in this version. Cards are pure image — no overlay, no text, no metadata. The aesthetic is deliberately mute. A museum wall label would be a different project.

"Is there a way to bookmark a specific image?"
No. The gallery is a walk, not a link collection. If you want to send someone to a specific image, send them the file and tell them which number to scroll to.

"Does the theme choice save?"
No. Every visit starts in dark mode. If you want the theme to persist, open the file and add a localStorage call inside the toggle handler — one line to save, one line to read on load. It's not built in because the design intent is that the gallery always opens in the same mood.

"Can I use this for a real museum?"
Yes. That's what it was built for. Point it at a folder of scanned artifacts, archival photographs, or exhibition prints, and it works. The only thing it can't do is handle thousands of images efficiently — beyond about 300, the DOM gets heavy enough that scrolling starts to feel slow. For anything larger, you'd want to convert it to virtual scrolling.

---

<div align="center">

📞 A question, an idea, a bug?

https://img.shields.io/badge/Email-mohamed005cheikh@gmail.com-d14836?style=flat-square&logo=gmail&logoColor=white
https://img.shields.io/badge/WhatsApp-+222_30_73_64_75-25D366?style=flat-square&logo=whatsapp&logoColor=white
https://img.shields.io/badge/GitHub-mohamed005cheikh--rgb-181717?style=flat-square&logo=github

<br />

One image. Then the next.

<sub>© 2026 Mohamed Cheikh — MC88</sub>

<br />
<br />

</div>