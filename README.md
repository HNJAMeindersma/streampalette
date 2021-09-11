# Stream Palette
Stream Palette is simple web GUI for playing audio streams. The interface can be configurated by drag & drop of your JSON configuration file on the palette. There are premade files available in the repository. The application runs fully client side (on HTML5, CSS5, JavaScript, Bootstrap 5.1) and it uses HTML5's Audio element to play streams.

### To-Do
- Volume control
- Configuration panel
  - Quick premade JSON configuration file access
  - GUI configuration for `showDarkButtons`
  - GUI configuration for `showTextOnly`
  - GUI configuration for `showIconsOnly`
- Alignment of buttons (including on mobile)

### JSON configuration file

##### Playlist
- `type`*: `stream` for buttons with a single stream channel, `group` for multiple stream channels.
- `order`*: integer for button order inside the palette.
- `name`*:  name for the button.
- `icon`: url directing to an icon for the button.
- `color`: background color for the button.
- `background`: url directing to a background image for the button.
- `showChannel`: `true` or `false` to display the button on the palette.
- `showIconOnly`: `true` to remove text from button when an icon is available.

For `type: stream`:
- `url`*: url directing to the stream.

For `type: group`:
- `streams`*: a list containing stream channel names and url's.
  - `key`: name for the button.
  - `value`: url directing to the stream.

_* = required configuration element_

##### Settings
- `showDarkButtons` when `true`: removes all icons and background (image and color) from the buttons.
- `showTextOnly` when `true`: removes all icons and background image, but leaves custom background color.
- `showIconsOnly` when `true`: removes all text from buttons when an icon is available.

### JSON file example
```
{
  "playlist": [
    {
      "type": "stream",
      "order": 1,
      "name": "NPO Radio 1",
      "url": "https://icecast.omroep.nl/radio1-bb-mp3",
      "icon": "https://upload.wikimedia.org/wikipedia/commons/d/da/NPO_Radio_1_logo_2014.svg",
      "color": "#021833",
      "background": "https://www.nporadio1.nl/svg/mainaccent_pattern.svg",
      "showChannel": true,
      "showIconOnly": false
    },
    {
      "type": "group",
      "order": 2,
      "name": "NPO Radio 2",
      "streams": {
        "NPO Radio 2":              "https://icecast.omroep.nl/radio2-bb-mp3",
        "NPO Radio 2 Soul & Jazz":  "https://icecast.omroep.nl/radio6-bb-mp3"
      },
      "icon": "https://upload.wikimedia.org/wikipedia/commons/f/f4/NPO_Radio_2_logo.svg",
      "color": "#22282e",
      "background": "https://www.nporadio2.nl/svg/footer_fill.svg",
      "showChannel": true,
      "showIconOnly": false
    }
  ],
  "settings": {
    "showDarkButtons": false,
    "showTextOnly": false,
    "showIconsOnly": false,
    "volume": 100
  }
}
```
