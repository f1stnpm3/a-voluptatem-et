English | [简体中文](./docs/README.zh.md)

# @f1stnpm3/a-voluptatem-et

A JavaScript library for parsing images. It obtains the mime type, size, and height-width information of the image according to the specifications of various types of images.

Available in Node.js and in the browser

## Supported file types

- png
- jpeg
- webp
- gif

## Install

```sh
npm i @f1stnpm3/a-voluptatem-et
```

## Example

Node.js

```javascript
import { parseImg, getMime } from '@f1stnpm3/a-voluptatem-et'

import fs from 'fs/promises'
import path from 'path'

const imgUrl = path.join(__dirname, './image/test.png')
const buff = await fs.readFile(imgUrl, { encoding: '' })

const result = parseImg(buff)
// => {mime: "image/png", size: 6219, width: 140, height: 32}

const type = getMime(buff)
// => 'image/png'
```

Browser

- html

```html
<input type="file" accept="image/*" onchange="handleChange(event)" />
```

- javascript

```javascript
import { parseImg, getMime } from '@f1stnpm3/a-voluptatem-et'

function handleChange(e) {
  const files = e.target.files
  const file = files[0]

  const reader = new FileReader()
  reader.readAsArrayBuffer(file)

  reader.onload = function (e) {
    const buf = e.target.result
    const typeArr = new Uint8Array(buf)

    const result = parseImg(typeArr)
    // => {mime: "image/png", size: 6219, width: 140, height: 32}

    const type = getMime(buff)
    // => 'image/png'
  }
}
```

## API

### parseImg(input)

#### input

Type: `Buffer | Uint8Array`

return an object(includes mime, size, width and height infomation)

### getMime(input)

return a string（for example：'image/png')
