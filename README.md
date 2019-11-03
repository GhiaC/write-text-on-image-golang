#### Example Add Persian/Arabic Text to image in Golang

<p align="right">
  <img src="image.jpg" title="WritePersianTextOnImageGolang">
</p>
<p align="left">
  <img src="new.jpg" title="WritePersianTextOnImageGolang">
</p>

```
import "github.com/ghiac/bimg
```

```go
buffer, err := bimg.Read("image.jpg")
if err != nil {
  fmt.Fprintln(os.Stderr, err)
}

addText := bimg.AddText{
  Text:       "هیچی نیستی",
  Top:        50,
  Left:       50,
  Opacity:    0.25,
  Width:      200,
  DPI:        100,
  Margin:     150,
  Font:       "sans bold 12",
  Background: bimg.Color{255, 255, 255},
}

newImage, err := bimg.NewImage(buffer).AddText(addText)
if err != nil {
  fmt.Fprintln(os.Stderr, err)
}

bimg.Write("new.jpg", newImage)
```

## Prerequisites

- [libvips](https://github.com/jcupitt/libvips) 7.42+ or 8+ (8.4+ recommended)
- C compatible compiler such as gcc 4.6+ or clang 3.0+
- Go 1.3+

**Note**: `libvips` v8.3+ is required for GIF, PDF and SVG support.

## Installation

```bash
go get -u github.com/ghiac/bimg
```

### libvips

Run the following script as `sudo` (supports OSX, Debian/Ubuntu, Redhat, Fedora, Amazon Linux):
```bash
curl -s https://raw.githubusercontent.com/h2non/bimg/master/preinstall.sh | sudo bash -
```

If you wanna take the advantage of [OpenSlide](http://openslide.org/), simply add `--with-openslide` to enable it:
```bash
curl -s https://raw.githubusercontent.com/h2non/bimg/master/preinstall.sh | sudo bash -s --with-openslide
```

The [install script](https://github.com/h2non/bimg/blob/master/preinstall.sh) requires `curl` and `pkg-config`.
