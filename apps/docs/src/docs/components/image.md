# Image

<ClientOnly>
  <Teleport to=".bd-toc">

[[toc]]

  </Teleport>
</ClientOnly>

<div class="lead mb-5">

Documentation and examples for opting images (via `<BImg>` component) into responsive behavior (so they never become larger than their parent elements), optionally adding lightweight styles to them — all via props.

</div>

BootstrapVueNext's image components support rounded images, thumbnail styling, alignment, and even the
ability to create blank images with an optional solid background color. Support for lazy loaded
images is available via the `lazy` prop.

## Image src resolving

The `src` prop and `blank-src` prop, out of the box, works only with absolute or fully-qualified-domain-name URLs. If you are using project assets as image sources, please refer to [Asset URL handling](https://github.com/vitejs/vite-plugin-vue/tree/main/packages/plugin-vue#asset-url-handling) to configure Vite to transform asset urls. If using a different build tool, you will need to find the relevant documentation to transform assets.

## Styling images

Several props are available for styling the rendered image element. The following sub-sections cover
the various options.

### Responsive images

Images in BootstrapVueNext can be made responsive with the `fluid` prop (which sets
`max-width: 100%; height: auto;` via CSS classes) so that it scales with the parent element - up to
the maximum native width of the image.

<HighlightCard>
  <BImg src="https://picsum.photos/1024/400/?image=41" fluid alt="Responsive image" />
  <template #html>

```vue-html
<BImg src="https://picsum.photos/1024/400/?image=41" fluid alt="Responsive image" />
```

  </template>
</HighlightCard>

To make a fluid image that will grow to fill the width of its container, use the `fluid-grow` prop.
Note this may cause blurring on small bitmap images.

<HighlightCard>
  <h5>Small image with <code>fluid</code>:</h5>
  <BImg src="https://picsum.photos/300/150/?image=41" fluid alt="Fluid image" />
  <h5 class="my-3">Small image with <code>fluid-grow</code>:</h5>
  <BImg src="https://picsum.photos/300/150/?image=41" fluid-grow alt="Fluid-grow image" />
  <template #html>

```vue-html
<h5>Small image with <code>fluid</code>:</h5>
<BImg src="https://picsum.photos/300/150/?image=41" fluid alt="Fluid image" />
<h5 class="my-3">Small image with <code>fluid-grow</code>:</h5>
<BImg src="https://picsum.photos/300/150/?image=41" fluid-grow alt="Fluid-grow image" />
```

  </template>
</HighlightCard>

Use the `block` prop to force the image to display as a block element rather than the browser
default of inline-block element.

### Image thumbnails

You can use prop `thumbnail` to give an image a rounded light border appearance.

<HighlightCard>
  <BRow>
    <BCol>
      <BImg thumbnail fluid src="https://picsum.photos/250/250/?image=54" alt="Image 1" />
    </BCol>
    <BCol>
      <BImg thumbnail fluid src="https://picsum.photos/250/250/?image=58" alt="Image 2" />
    </BCol>
    <BCol>
      <BImg thumbnail fluid src="https://picsum.photos/250/250/?image=59" alt="Image 3" />
    </BCol>
  </BRow>
  <template #html>

```vue-html
<BRow>
  <BCol>
    <BImg thumbnail fluid src="https://picsum.photos/250/250/?image=54" alt="Image 1" />
  </BCol>
  <BCol>
    <BImg thumbnail fluid src="https://picsum.photos/250/250/?image=58" alt="Image 2" />
  </BCol>
  <BCol>
    <BImg thumbnail fluid src="https://picsum.photos/250/250/?image=59" alt="Image 3" />
  </BCol>
</BRow>
```

  </template>
</HighlightCard>

### Rounded corners

You can control which corners are rounded by setting the rounded prop to one of the following
values:

- `true` (or prop present with no value): round all corners
- `false` (or prop not present): no explicit rounding or corners (default)
- `'top'`: round the top corners
- `'end'`: round the right corners
- `'bottom'`: round the bottom corners
- `'start'`: round the left corners
- `'circle'`: make a circle (if square image) or oval (if not square) border
- `'0'`: explicitly turn off rounding of corners

<HighlightCard>
  <div class="d-flex gap-2">
    <BImg v-bind="mainProps" rounded alt="Rounded image" />
    <BImg v-bind="mainProps" rounded="top" alt="Top-rounded image" />
    <BImg v-bind="mainProps" rounded="end" alt="Right-rounded image" />
    <BImg v-bind="mainProps" rounded="bottom" alt="Bottom-rounded image" />
    <BImg v-bind="mainProps" rounded="start" alt="Left-rounded image" />
    <BImg v-bind="mainProps" rounded="circle" alt="Circle image" />
    <BImg v-bind="mainProps" rounded="0" alt="Not rounded image" />
  </div>
  <template #html>

```vue
<template>
  <BImg v-bind="mainProps" rounded alt="Rounded image" />
  <BImg v-bind="mainProps" rounded="top" alt="Top-rounded image" />
  <BImg v-bind="mainProps" rounded="end" alt="Right-rounded image" />
  <BImg v-bind="mainProps" rounded="bottom" alt="Bottom-rounded image" />
  <BImg v-bind="mainProps" rounded="start" alt="Left-rounded image" />
  <BImg v-bind="mainProps" rounded="circle" alt="Circle image" />
  <BImg v-bind="mainProps" rounded="0" alt="Not rounded image" />
</template>

<script setup lang="ts">
const mainProps = {
  blank: true,
  blankColor: '#777',
  width: 75,
  height: 75,
  class: 'm1',
}
</script>
```

  </template>
</HighlightCard>

### Aligning images

Align images with the boolean props `left` (floats left) `right`(floats right), and `center` (auto
left+right margins). You can also center images by placing them in a container that has the class
`text-center`.

**Left and right aligned (float):**

<HighlightCard>
  <div class="clearfix">
    <BImg left src="https://picsum.photos/125/125/?image=58" alt="Left image" />
    <BImg right src="https://picsum.photos/125/125/?image=58" alt="Right image" />
  </div>
  <template #html>

```vue-html
<BImg left src="https://picsum.photos/125/125/?image=58" alt="Left image" />
<BImg right src="https://picsum.photos/125/125/?image=58" alt="Right image" />
```

  </template>
</HighlightCard>

**Center aligned (block):**

<HighlightCard>
  <BImg center src="https://picsum.photos/125/125/?image=58" alt="Center image" />
  <template #html>

```vue-html
<BImg center src="https://picsum.photos/125/125/?image=58" alt="Center image" />
```

  </template>
</HighlightCard>

Note: `left` takes precedence over `right` which takes precedence over `center`.

## Blank (or solid color) images

`<BImg>` provides built-in support for generating blank images (transparent by default) of any
width and height, by setting the `blank` prop, and specifying `width` and `height` values (in
pixels). You can apply any of the other `<BImg>` props to change the style/behavior of the
generated image.

Use the `blank-color` prop to set the blank image color. The `blank-color`prop can accept any CSS
color value:

- Named colors — i.e. `orange` or `blue`
- Hex colors — i.e. `#FF9E2C`
- RGB and RGBa colors — i.e. `rgb(255, 158, 44)` and `rgba(255, 158, 44, .5)`
- HSL and HSLa colors — i.e. `hsl(32, 100%, 59%)` and `hsla(32, 100%, 59%, .5)`

The default `blank-color` is `transparent`.

<HighlightCard>
  <div class="d-flex gap-2">
    <BImg v-bind="propsTr" alt="Transparent image" />
    <BImg v-bind="propsTr" blank-color="#777" alt="HEX shorthand color image (#777)" />
    <BImg v-bind="propsTr" blank-color="red" alt="Named color image (red)" />
    <BImg v-bind="propsTr" blank-color="black" alt="Named color image (black)" />
    <BImg v-bind="propsTr" blank-color="#338833" alt="HEX color image" />
    <BImg v-bind="propsTr" blank-color="rgba(128, 255, 255, 0.5)" alt="RGBa color image" />
    <BImg v-bind="propsTr" blank-color="#88f" alt="HEX shorthand color (#88f)" />
  </div>
  <template #html>

```vue
<template>
  <BImg v-bind="propsTr" alt="Transparent image" />
  <BImg v-bind="propsTr" blank-color="#777" alt="HEX shorthand color image (#777)" />
  <BImg v-bind="propsTr" blank-color="red" alt="Named color image (red)" />
  <BImg v-bind="propsTr" blank-color="black" alt="Named color image (black)" />
  <BImg v-bind="propsTr" blank-color="#338833" alt="HEX color image" />
  <BImg v-bind="propsTr" blank-color="rgba(128, 255, 255, 0.5)" alt="RGBa color image" />
  <BImg v-bind="propsTr" blank-color="#88f" alt="HEX shorthand color (#88f)" />
</template>

<script setup lang="ts">
const propsTr = {
  blank: true,
  width: 75,
  height: 75,
  class: 'm1',
}
</script>
```

  </template>
</HighlightCard>

**Notes:**

- In blank image mode, if only one of width or height is set, the image will have both width and
  height set to the same value
- In blank image mode, if width and height are not set, both width and height will internally be set
  to 1
- The `blank` prop takes precedence over the `src` prop. If you set both and later set `blank` to
  `false` the image specified in `src` will then be displayed
- Blank images are rendered using SVG image data URLs
- The `width` and `height` props will also apply the `width` and `height` attributes to the rendered
  `<img>` tag, even if `blank` is not set

## `srcset` support

`<BImg>` supports the
[`srcset` and `sizes` attributes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#attr-srcset)
on images. The props accept either a string value, or an array of strings (the array of strings will
be converted into a single string separated by commas).

For details on usage of these attributes, refer to
[MDN's Responsive Images](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images)
guide.

**Notes:**

- If the `blank` prop is set, then `srcset` and `sizes` props are ignored
- IE 11 does not support `srcset` and `sizes`, so ensure you have a value for the `src` prop
- Vue-loader does not support project relative URLs (asset URLs) on the `srcset` attribute; instead
  use `require(...)` to resolve the individual URL paths. Be cautious of creating a string of data
  URI's longer than supported by the maximum attribute value length of the browser. If your webpack
  config has a limit for the `url-loader` and you want to prevent inline data-urls, you may have to
  overwrite the loader limits: `require('!!url-loader?limit=0!./assets/photo.jpg')`
- Support for `srcset` and `sizes` was added in release `2.1.0`

## Lazy loaded images

Lazy loaded images are actived through the `lazy` prop. Eventually, the component will be expanded to include placeholder slots, but are not available at this time.

<ComponentReference :data="data" />

<script setup lang="ts">
import {data} from '../../data/components/image.data'
import ComponentReference from '../../components/ComponentReference.vue'
import HighlightCard from '../../components/HighlightCard.vue'
import {BRow, BCol, BCard, BCardBody, BImg} from 'bootstrap-vue-next'
import {ref, computed} from 'vue'

const mainProps = {blank: true, blankColor: '#777', width: 75, height: 75, class: 'm1'}
const propsTr = {blank: true, width: 75, height: 75, class: 'm1'}
</script>
