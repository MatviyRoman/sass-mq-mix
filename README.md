# sass-mq-mix

<h1>sass media queries mixin</h1>

[![Donate](https://www.paypalobjects.com/en_US/i/btn/btn_donate_SM.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=E2H8329XLYRKQ&source=url)
[![Version](https://img.shields.io/npm/v/sass-mq-mix.svg)](http://npm.im/sass-mq-mix)
[![Downloads](https://img.shields.io/npm/dm/sass-mq-mix.svg)](http://npm.im/sass-mq-mix)

Mixins for checking **group of devices** (mobile, tablet, laptop, desktop) or **device by name** (iPhone 5, iPhone X, iPhone 11 Pro Max, iPad Pro 12.9, etc). Expandable and very simple for usage.

### Helpful Links

- [Demo](http://scss-mq-mix.matviy.pp.ua)

### Important

> Don't check the adaptability in the browser DevTools, there are [incorrectly calculated dimensions](https://codepen.io/matviy/pen/ZEQOrmv) of the sides in the landscape orientation of the device.
> It is better to check on a real device or in a simulator (for example, xCode Simulator).

> Use [group-css-media-queries](https://github.com/Se7enSky/group-css-media-queries) to optimize media queries. Without it, a lot of the same `@media ...` code is generated, especially if for the sake of convenience to use the mixin `@include device()` in each selector separately. Wrapper for Gulp - [gulp-group-css-media-queries](https://github.com/avaly/gulp-group-css-media-queries).

## Table of Contents

- [Installation](#installation)
- [Documentation](#documentation)
  - [Examples](#examples)
  - [List of supported devices](#list-of-supported-devices)
  - [Expanding the list of devices](#expanding-the-list-of-devices)
- [Credits](#credits)
- [License](#license)
- [Donate](#donate)

## Installation

```bash
$ git clone https://github.com/MatviyRoman/sass-mq-mix.git
or
$ npm install sass-mq-mix
or
$ curl -O https://raw.githubusercontent.com/MatviyRoman/sass-mq-mix/master/_sass-mq-mix.scss
```

## Documentation

Include mixins to app:

```scss
@import "sass-mq-mix/mq";
```

### Examples:

It can be used like this:

```scss
@include device(iPhone5, portrait) {
  // portrait orientation
  // iPhone 5, iPhone 5s, iPhone 5c, iPhone SE
}
@include device(iPhone6Plus iPhoneXR, landscape) {
  // landscape orientation
  // iPhone 6+, iPhone 6s+, iPhone 7+, iPhone 8+, iPhone XR, iPhone 11
}
@include device(iPadPro10 iPadPro11 iPadPro12) {
  // all orientations
  // iPad Pro 10.5, iPad Pro 11, iPad Pro 12.9
}
```

Or like this:

```scss
@include device(desktop) {
  // all orientations
  // desktop
}
@include device(mobile tablet laptop, landscape) {
  // landscape orientation
  // mobile, tablet, laptop
}
```

Or even like this:

```scss
@include device(mobile-landscape tablet laptop) {
  // landscape orientation
  // mobile

  // all orientations
  // tablet, laptop
}
@include device(mobile-landscape tablet laptop, portrait) {
  // landscape orientation
  // mobile

  // portrait orientation
  // tablet, laptop
}
```

Examples

```scss
Before @include screen(320px, 768px, portrait) {
  .test {
    width: 100%;
  }
}

After
  @media
  only
  screen
  and
  (min-width: 320px)
  and
  (max-width: 768px)
  and
  (orientation: portrait) {
  .test {
    width: 100%;
  }
}
```

```scss
Before @include screen(768px, 320px, landscape) {
  .test {
    width: 100%;
  }
}

After
  @media
  only
  screen
  and
  (min-width: 320px)
  and
  (max-width: 768px)
  and
  (orientation: portrait) {
  .test {
    width: 100%;
  }
}
```

```scss
Before @include screen(0, 325px) {
  .test {
    width: 100%;
  }
}

After @media only screen and (max-width: 325px) {
  .test {
    width: 100%;
  }
}
```

```scss
Before @include screen(325px) {
  .test {
    width: 100%;
  }
}

After @media only screen and (min-width: 325px) {
  .test {
    width: 100%;
  }
}
```

```scss
Before @include screen-height(100vh, portrait) {
  .test {
    width: 100%;
  }
}

After @media only screen and (min-height: 100vh) and (orientation: portrait) {
  .test {
    width: 100%;
  }
}
```

```scss
Before @include max-screen-height(100vh, landscape) {
  .test {
    width: 100%;
  }
}

After @media only screen and (max-height: 100vh) and (orientation: portrait) {
  .test {
    width: 100%;
  }
}
```

There are also common mixins:

```scss
@include screen(min-width, max-width, orientation) {
  /*...*/
}
@include screen(min-width, max-width, orientation) {
  /*...*/
}
@include min-screen(width) {
  /*...*/
}
@include max-screen(width) {
  /*...*/
}

@include screen-height(min-height, max-height, orientation) {
  /*...*/
}
@include min-screen-height(height) {
  /*...*/
}
@include max-screen-height(height) {
  /*...*/
}

@include landscape() {
  /*...*/
}
@include portrait() {
  /*...*/
}
```

### List of supported devices:

#### Groups

- Mobiles 320-767px `mobile` `mobile-portrait` `mobile-landscape`
- Tablets 768-1023px `tablet` `tablet-portrait` `tablet-landscape`
- Laptops 1024-1199px `laptop` `laptop-portrait` `laptop-landscape`
- Desktop >=1200px `desktop` `desktop-portrait` `desktop-landscape`

#### Phones

- iPhone 5, 5s, 5c, SE `iphone5` `iphone5s` `iphone5c` `iphonese`
- iPhone 6, 6s, 7, 8 `iphone6` `iphone6s` `iphone7` `iphone8`
- iPhone 6+, 6s+, 7+, 8+ `iphone6plus` `iphone6splus` `iphone7plus` `iphone8plus`
- iPhone X, XS, 11 Pro `iphonex` `iphonexs` `iphone11pro`
- iPhone XR, 11 `iphonexr` `iphone11`
- iPhone XS Max, 11 Pro Max `iphonexsmax` `iphone11promax`

#### Tablets

- iPad 1, 2, Mini, Air `ipad1` `ipad2` `ipadmini` `ipadair`
- iPad 3, 4, Pro 9.7" `ipad3` `ipad4` `ipadpro9`
- iPad Pro 10.5" `ipadpro10`
- iPad Pro 11.0" `ipadpro11`

#### Laptops

- iPad Pro 12.9" `ipadpro12`

_Well, Yes. iPad Pro 12.9" is a laptop because of its size._

---

### Expanding the list of devices:

You can add support for custom devices or group of devices without editing the source.
Before `@import "sass-mq-mix/_sass-mq-mix"`, you must specify `$ms-devices` variable with a list of additional devices:

```scss
$ms-devices: (
  desktop-sm: (
    group: true,
    // group of devices
      min: 1200px,
    max: 1919px
  ),
  desktop-md: (
    group: true,
    // group of devices
      min: 1920px,
    max: 2879px
  ),
  desktop-lg: (
    group: true,
    // group of devices
      min: 2880px
  ),
  pixel2xl: (
    group: false,
    // specific device
      width: 411px,
    // or 412px?..
      height: 823px,
    pixel-ratio: 3.5
  ),
  macbook12: (
    group: false,
    // specific device
      orientation: landscape,
    width: 1440px,
    height: 900px,
    pixel-ratio: 2
  ),
  imac27: (
    group: false,
    // specific device
      orientation: landscape,
    width: 5120px,
    height: 2880px
  )
);
```

## Credits

- [Roman Matviy](https://matviy.pp.ua)

## License

This software is open-source licensed under the [MIT license](https://opensource.org/licenses/MIT).

## Donate

Buy me a coffee :)

QR Code <img src="https://github.com/MatviyRoman/sass-mq-mix/blob/master/img/qr-code.png?raw=true" alt="donation sass-mq-mix">

<form action="https://www.paypal.com/cgi-bin/webscr" method="post" target="_top">
<input type="hidden" name="cmd" value="_s-xclick" />
<input type="hidden" name="hosted_button_id" value="E2H8329XLYRKQ" />
<input type="image" src="https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif" name="submit" title="PayPal - The safer, easier way to pay online!" alt="Donate with PayPal button" />
<img alt="" src="https://www.paypal.com/en_UA/i/scr/pixel.gif" width="1" height="1" />
</form>

Thank You!
