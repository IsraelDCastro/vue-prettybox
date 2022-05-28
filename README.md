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

Accepted
props: `animation, imageUrl, alt, isRounded/is-rounded, isCircled/is-circled, hasShadow/has-shadow, figcaption, and bgBackdropClose`.

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
