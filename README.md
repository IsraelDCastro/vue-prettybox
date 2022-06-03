# Vue Prettybox

It is a tool dependency that allows you to open or zoom image just by click it. It helps you to view the image to have a
better look of it without making zoom in on your browser.

### Installation

You can install vue-prettybox using `yarn add vue-prettybox` or `npm install vue-prettybox`.

#### Import components

You can import the components with the following code:

```bash
import {
  SingleImage,
  ImageGallery
} from "vue-prettybox/components";
```

#### Import CSS/SCSS

You can import the CSS or SCSS with the following code:

```bash 
@import "vue-prettybox/main.css";
```

```bash
@import "vue-prettybox/main.min.css";
```

```bash
@import "vue-prettybox/main.scss";
```

### Single image

With this component, you can zoom in on an image to see it near and better view it.

```bash 
<SingleImage
  animation="..." imageUrl="..." alt="..."
  is-rounded has-shadow figcaption="..."
  bg-backdrop-close
/>
```

Accepted props: `animation, imageUrl, alt, isRounded/is-rounded, isCircled/is-circled, hasShadow/has-shadow, figcaption, and bgBackdropClose`.

<table>
  <thead>
    <tr>
      <th>Prop</th>
      <th>Type</th>
      <th>Default</th>
      <th>Comment</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>imageUrl</td>
      <td>String</td>
      <td>https://picsum.photos/1280/720?random</td>
      <td>URL for the image to zoom in.</td>
    </tr>
    <tr>
      <td>animation</td>
      <td>String</td>
      <td>fade</td>
      <td>Animation to open modal with the image.</td>
    </tr>
    <tr>
      <td>alt</td>
      <td>String</td>
      <td>Empty</td>
      <td>Alt text for the image.</td>
    </tr>
    <tr>
      <td>isRounded</td>
      <td>Boolean</td>
      <td>false</td>
      <td>Add little rounded corners.</td>
    </tr>
    <tr>
      <td>isCircled</td>
      <td>Boolean</td>
      <td>false</td>
      <td>
        Make a circle with the image, it works better with a square image.
      </td>
    </tr>
    <tr>
      <td>hasShadow</td>
      <td>Boolean</td>
      <td>false</td>
      <td>Add a little shadow to the image.</td>
    </tr>
    <tr>
      <td>figcaption</td>
      <td>String</td>
      <td>Empty</td>
      <td>
        Add figcaption text to image, it is visible only when you open the image.
      </td>
    </tr>
    <tr>
      <td>bgBackdropClose</td>
      <td>Boolean</td>
      <td>false</td>
      <td>You can close the image modal by clicking the background.</td>
    </tr>
  </tbody>
</table>

### Image gallery

Image gallery component you can zoom in on an image to see it near and better view it, also you have a slider in the modal to see other ones.

```bash 
<ImageGallery
  animation="..." imageUrl="..."
  is-rounded has-shadow
/>
```

Accepted props: `animation, imagesUrl, isRounded/is-rounded, isCircled/is-circled, hasShadow/has-shadow, squared, figcaption, columns, mdColumns, xsColumns, space and bgBackdropClose`.

imagesUrl structure:
```bash
[{ img: "...", alt: "...", figcaption: "..." }]
```

<table>
  <thead>
    <tr>
      <th>Prop</th>
      <th>Type</th>
      <th>Default</th>
      <th>Comment</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>imagesUrl</td>
      <td>Array</td>
      <td>8 random Picsum photos</td>
      <td>
        URLs for the images to zoom in. Structure below:
      </td>
    </tr>
    <tr>
      <td>animation</td>
      <td>String</td>
      <td>fade</td>
      <td>Animation to open modal with the image.</td>
    </tr>
    <tr>
      <td>isRounded</td>
      <td>Boolean</td>
      <td>false</td>
      <td>Add little rounded corners.</td>
    </tr>
    <tr>
      <td>isCircled</td>
      <td>Boolean</td>
      <td>false</td>
      <td>
        Make a circle with the image, it works better with a square image.
      </td>
    </tr>
    <tr>
      <td>hasShadow</td>
      <td>Boolean</td>
      <td>false</td>
      <td>Add a little shadow to the images.</td>
    </tr>
    <tr>
      <td>squared</td>
      <td>Boolean</td>
      <td>false</td>
      <td>All images are squared.</td>
    </tr>
    <tr>
      <td>columns</td>
      <td>Number</td>
      <td>4</td>
      <td>Quantity of columns on desktop.</td>
    </tr>
    <tr>
      <td>mdColumns</td>
      <td>Number</td>
      <td>3</td>
      <td>Quantity of columns on tablet.</td>
    </tr>
    <tr>
      <td>xsColumns</td>
      <td>Number</td>
      <td>2</td>
      <td>Quantity of columns on mobile.</td>
    </tr>
    <tr>
      <td>space</td>
      <td>String</td>
      <td>20px</td>
      <td>
        Gap space for each column, you can use <strong>px, rem, em</strong>,
        etc.
      </td>
    </tr>
    <tr>
      <td>bgBackdropClose</td>
      <td>Boolean</td>
      <td>false</td>
      <td>You can close the image modal by clicking the background.</td>
    </tr>
  </tbody>
</table>
