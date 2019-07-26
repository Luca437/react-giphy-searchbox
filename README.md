# React Giphy Searchbox

[![Travis][build-badge]][build]
[![npm package][npm-badge]][npm]
[![Codecov][codecov-badge]][Codecov]

Responsive and customizable search and select for Giphy's GIFs.

> **Note:** The searchbox shows the user trending GIFs, switching to searched results once the user starts typing something in the search field.

<img width="305" style="position:relative; left: -14px" alt="react-giphy-searchbox-screen" src="https://user-images.githubusercontent.com/2235134/61870847-77a8c500-aedf-11e9-8e48-08171560e0ab.png">

[![Edit react-giphy-searchbox](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/react-giphy-searchbox-l8dxc?fontsize=14)

## Getting started

### Installation

```
yarn add react-giphy-searchbox
```

```
npm install react-giphy-searchbox --save
```

### Basic Example

```javascript
import React from 'react'
import { render } from 'react-dom'
import ReactGiphySearchbox from 'react-giphy-searchbox'

const App = () => (
  <ReactGiphySearchbox
    apiKey="YOUR_API_KEY" // Required: get your on https://developers.giphy.com
    onSelect={item => console.log(item)}
  />
)

render(<App />, document.getElementById("root"))
```

### Props

| Prop                   | Type     | Desc                                                                                                                                                                                                            |
| ---------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `apiKey`               | string   | **REQUIRED:** Giphy's API key. Get your on https://developers.giphy.com.                                                                                                                                         |
| `onSelect`             | function | **REQUIRED** A callback which is triggered whenever a GIF is selected. It returns a Gif object in the format specified for an image from Giphy's API.                                                            |
| `rating`               | string   | Filters results by [specified rating](https://developers.giphy.com/docs/optional-settings/#rating). <br />*Default:* `g`                                                                                        |
| `gifPerPage`           | number   | The maximum number of images to return per page. <br />*Default:* `20`                                                                                                                                          |
| `masonryConfig`        | array    | An array of objects describing the masonry's properties at different breakpoints. [See specific chapter for further info.](#responsive-options) <br />*Default:* `[{ columns: 2, imageWidth: 120, gutter: 5 }]` |
| `gifListHeight`        | string   | The height of the returned GIF list. <br />*Default:* `300px`                                                                                                                                                    |
| `messageError`         | string   | Generic errror message when APIs call fails. <br />*Default:* `Oops! Something went wrong. Please, try again.`                                                                                                  |
| `messageLoading`       | string   | Loading message only for accessibility purposes. <br />*Default:* `Loading...`                                                                                                                                  |
| `messageNoMatches`     | string   | Message to tell users searched string returned empty array. <br />*Default:* `No matches found.`                                                                                                                |
| `loadingImage`         | string   | If you want to customize the loading spinner, use this prop to set an alternative `src` for the image.                                                                                                          |
| `poweredByGiphy`       | boolean  | You can choose to display or not display the **Powered by Giphy** badge at the bottom. Note that you need to show it if you want a production Api key from Giphy. <br />*Default:* `true`                       |
| `poweredByGiphyImage`  | string   | If you want to customize the **Powered by Giphy** badge, use this prop to set an alternative `src` for the image.                                                                                               |
| `searchPlaceholder`    | string   | Search input placeholder. <br />*Default:* `Search for GIFs`                                                                                                                                                    |
| `wrapperClassName`     | string   | Additional CSS class for the `<div>` that wrap the whole component.                                                                                                                                              |
| `searchFormClassName`  | string   | Additional CSS class for the `<form>` element.                                                                                                                                                                   |
| `listWrapperClassName` | string   | Additional CSS class for the `<div>` that wrap the GIFs list.                                                                                                                                                    |
| `listItemClassName`    | string   | Additional CSS class for the `<button>` that wrap the single image.                                                                                                                                              |

### Responsive options
`masonryConfig` prop allow you to define responsiveness of the component. This prop accept an array of objects describing the masonry's properties at different breakpoints.

Each `object` in the array has the following properties:

| Prop         | Type   | Description                                                       |
| ------------ | ------ | ----------------------------------------------------------------- |
| `mq`         | string | The minimum viewport width                                        |
| `columns`    | number | The number of vertical columns                                    |
| `imageWidth` | number | The width (in px) of the image, and consequentially of the column |
| `gutter`     | number | The space (in px) between the columns                             |


```javascript
[
  { columns: 2, imageWidth: 140, gutter: 10 },
  { mq: '700px', columns: 3, imageWidth: 200, gutter: 10 },
  { mq: '1000px', columns: 4, imageWidth: 220, gutter: 10 },
]
```

When defining your properties, note the following:
- properties must be listed **smallest to largest breakpoints** in a mobile first approach;
- The size without the `mq` property is assumed to be your **smallest breakpoint, and must appear first.**

## License
MIT. © 2019 Sergio Pedercini

[build-badge]: https://img.shields.io/travis/sergiop/react-giphy-searchbox?style=flat-square
[build]: https://travis-ci.org/sergiop/react-giphy-searchbox

[npm-badge]: https://img.shields.io/npm/v/react-giphy-searchbox?style=flat-square
[npm]: https://www.npmjs.org/package/react-giphy-searchbox

[codecov-badge]: https://img.shields.io/codecov/c/github/sergiop/react-giphy-searchbox?style=flat-square&token=c22b785c904542cfa751e2ff255e1180
[Codecov]: https://codecov.io/gh/sergiop/react-giphy-searchbox
