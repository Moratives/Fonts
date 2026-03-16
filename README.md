# Dynamic Masterclass Landing Page Injector

This repository contains `script.js`, a JavaScript utility that **injects a complete marketing landing page section stack** into an existing webpage.

It is designed for **webinar funnels, masterclass pages, and marketing pages** where you want to dynamically add sections without editing the original page HTML.

The script automatically:

* Adds a **fixed countdown banner**
* Injects **marketing sections**
* Loads **styles and fonts**
* Handles **image fallbacks**
* Integrates with **WebinarJam embed buttons**
* Runs a **rolling 15-minute countdown timer**

---

# Features

### Dynamic Content Injection

The script injects multiple landing page sections including:

* Media / "As Seen In" logos
* Testimonials
* Pain point sections
* Benefit cards
* Call-to-action blocks
* Image galleries
* Speaker bio section
* Final testimonial

All content is generated dynamically using JavaScript.

---

### Rolling Countdown Timer

A fixed banner appears at the top of the page:

```
Spots are limited! Next Masterclass starts in: 00:14:32
```

The timer always counts down to the **next 15-minute interval**.

Example:

```
10:03 → 10:15
10:15 → 10:30
10:30 → 10:45
```

This creates **continuous urgency for webinar registrations**.

---

# Installation

Add the script to any page.

```html
<script src="script.js"></script>
```

Or load from GitHub Pages:

```html
<script src="https://yourdomain.github.io/script.js"></script>
```

---

# Required Dependency

The script expects **jQuery** to already be loaded on the page.

Example:

```html
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
```

---

# Configuration

At the top of the script you must configure the **image base path**.

```javascript
var IMG_BASE = 'https://yourdomain.github.io/images';
```

All images used by the injected sections will load from this folder.

Example structure:

```
images/
  as-seen-in.png
  cheryl-avatar.png
  check1.png
  check2.png
  check3.png
  final-Testimony.png
  final-Testimony-mobile.png
  dm-conversation.png
  theresa-bio.png
  masterclass-preview.webp
  brenda-avatar.png
```

---

# Editing the Page Content

All landing page content is generated inside the function:

```
getSectionsHTML()
```

Inside `script.js` you will find:

```javascript
function getSectionsHTML() {
```

This function returns a **large HTML string** containing all sections.

Example:

```javascript
return '' +

'<div class="cb-section cb-bg-cream" id="asSeen">' +
  '<div class="cb-container cb-text-center">' +
    '<div class="cb-logo-bar">' +
      '<img src="' + I + '/as-seen-in.png">' +
    '</div>' +
  '</div>' +
'</div>' +
```

To edit page content, modify the HTML inside this function.

---

# Common Content Edits

## 1. Change Headline Text

Example:

```javascript
<h2 class="cb-heading cb-h2">
You have a successful career... but you hate it.
</h2>
```

You can edit this directly.

---

## 2. Change Testimonials

Find sections like:

```
SECTION 2: Cheryl Testimonial
SECTION 11: Brenda Final Testimonial
```

Edit the quote text:

```javascript
<p>"I didn't realize how much I would actually learn..."</p>
```

---

## 3. Change Speaker Bio

Find:

```
SECTION 9: About Theresa Bio
```

Edit the paragraphs to match the speaker.

Example:

```javascript
<p>Hi! I'm Theresa, Career Clarity Expert.</p>
```

---

## 4. Change Images

All images use this format:

```javascript
<img src="' + I + '/image-name.png">
```

Where `I` equals `IMG_BASE`.

To change an image:

1. Upload a new image to the `/images` folder
2. Update the filename.

Example:

```
/images/new-speaker-photo.png
```

Then update:

```javascript
<img src="' + I + '/new-speaker-photo.png">
```

---

## 5. Change Call-To-Action Button Text

Example:

```javascript
<a onclick="register()" class="cb-btn">Save my seat →</a>
```

You can modify the text:

```
Save my seat
Register now
Join the masterclass
Reserve your spot
```

---

# Webinar Registration Button

The script includes a function:

```javascript
register()
```

This triggers the embedded WebinarJam registration button:

```javascript
$("button.wj-embed-button.js-embed-button").click()
```

All CTA buttons call this function.

Example:

```html
<a onclick="register()">Save my seat</a>
```

---

# Countdown System

The countdown timer is controlled by:

```
startQuarterCountdown()
```

The script calculates the **next 15-minute mark** and counts down to it.

Example logic:

```
Current Time → Find next quarter hour
Countdown → Update every second
When timer hits zero → jump to next interval
```

---

# Image Error Protection

If an image fails to load, the script automatically replaces it with a placeholder:

```
Image unavailable in your region
```

This prevents layout breakage if CDN or regional blocking occurs.

---

# Where the Sections Are Injected

The script tries to insert sections after:

```
#js-header-section
```

If not found it falls back to:

```
#js-content-section
.content_area
.d-flex.flex-column
document.body
```

---

# Customization Tips

You can easily customize this script by:

* Changing section order
* Adding new sections
* Editing CSS styles
* Updating countdown messaging
* Replacing testimonials

Most design styles are defined in:

```
getStyles()
```

---

# File Structure

```
project
│
├── script.js
├── Belluga1.ttf
├── FontsFree-Net-belluga.ttf
├── README.md
└── images/
```

---

# Use Cases

This script works well for:

* Webinar funnels
* Masterclass registration pages
* Coaching landing pages
* Marketing pages injected into existing CMS pages
* Pages where HTML editing is limited

---
