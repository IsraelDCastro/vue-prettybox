<script>
const randomNumber = Math.ceil(Math.random() * 200);
</script>

<script setup>
import Close from './icons/close'
import Left from '@/components/icons/left.vue'
import Right from '@/components/icons/right.vue'

const openImageGalleryBox = ref(false)
const position = ref(0)

const openCloseImageGalleryBox = (indexPosition) => {
  openImageGalleryBox.value = !openImageGalleryBox.value
  position.value = indexPosition
}

const image_gallery_masonry = ref(null);
const imageGalleryWidth = ref(null)
const imageGalleryHeight = ref(null)

const closeBackdrop = () => props.bgBackdropClose ? openImageGalleryBox.value = !openImageGalleryBox.value : null
const prev = () => position.value -= 1;
const next = () => position.value += 1;
const props = defineProps({
  imagesUrl: {
    type: Array,
    default: [
      { img: `https://picsum.photos/1280/720?random=${randomNumber + 1}`, alt: 'Lorem ipsum', figcaption: 'Lorem ipsum dolor sit amet' },
      { img: `https://picsum.photos/720/1280?random=${randomNumber + 2}`, alt: 'Lorem ipsum', figcaption: 'Lorem ipsum dolor sit amet' },
      { img: `https://picsum.photos/720/720?random=${randomNumber + 3}`, alt: 'Lorem ipsum', figcaption: 'Lorem ipsum dolor sit amet' },
      { img: `https://picsum.photos/1280/720?random=${randomNumber + 4}`, alt: 'Lorem ipsum', figcaption: 'Lorem ipsum dolor sit amet' },
      { img: `https://picsum.photos/720/720?random=${randomNumber + 5}`, alt: 'Lorem ipsum', figcaption: 'Lorem ipsum dolor sit amet' },
      { img: `https://picsum.photos/720/1280?random=${randomNumber + 6}`, alt: 'Lorem ipsum', figcaption: 'Lorem ipsum dolor sit amet' },
      { img: `https://picsum.photos/1280/720?random=${randomNumber + 7}`, alt: 'Lorem ipsum', figcaption: 'Lorem ipsum dolor sit amet' },
      { img: `https://picsum.photos/720/1280?random=${randomNumber + 8}`, alt: 'Lorem ipsum', figcaption: 'Lorem ipsum dolor sit amet' }
    ],
    required: true
  },
  animation: {
    type: String,
    default: 'fade',
    required: true
  },
  isRounded: {
    type: Boolean,
    default: false
  },
  isCircled: {
    type: Boolean,
    default: false
  },
  hasShadow: {
    type: Boolean,
    default: false
  },
  bgBackdropClose: {
    type: Boolean,
    default: false
  },
  columns: {
    type: Number,
    default: 4
  },
  mdColumns: {
    type: Number,
    default: 3
  },
  xsColumns: {
    type: Number,
    default: 2
  },
  space: {
    type: String,
    default: "20px"
  },
})

onMounted (() => {
  imageGalleryWidth.value = image_gallery_masonry.value[0].clientWidth;
  imageGalleryHeight.value = image_gallery_masonry.value[0].clientHeight;
})
</script>
<template>
  <div
    class="image-galley-masonry-wrap"
  >
    <figure v-for="(image, index) in props.imagesUrl" :key="index" class="image-gallery-masonry">
      <img
        :src="image.img"
        :alt="image.alt"
        class="image"
        :class="[
          {'is-rounded': props.isRounded },
          {'is-circled': props.isCircled },
          {'has-shadow': props.hasShadow }
        ]"
        ref="image_gallery_masonry"
        :width="imageGalleryHeight"
        :height="imageGalleryHeight"
        loading="lazy"
        @click="openCloseImageGalleryBox(index)"
      >
    </figure>
    <Transition :name="props.animation" mode="out-in">
      <div v-if="openImageGalleryBox" class="image-galley-prettybox">
        <Transition name="backdrop" mode="out-in" appear>
          <div
            class="bg-backdrop"
            @click="closeBackdrop"
          />
        </Transition>
        <button class="close-button" @click="openCloseImageGalleryBox">
          <Close />
        </button>
        <button
          class="left-button"
          :disabled="position === 0"
          @click="prev"
        >
          <Left />
        </button>
        <button
          class="right-button"
          :disabled="position === props.imagesUrl.length - 1"
          @click="next"
        >
          <Right />
        </button>
        <template v-for="(image, indexImg) in props.imagesUrl" :key="indexImg">
          <TransitionGroup name="slider-item" mode="out-in">
            <figure
              v-if="indexImg === position"
              :key="indexImg"
              class="image-gallery"
            >
              <img
                :src="image.img"
                :alt="image.alt"
                class="image"
                :class="[
                  {'is-rounded': props.isRounded },
                  {'is-circled': props.isCircled },
                  {'has-shadow': props.hasShadow }
                ]"
                loading="lazy"
              >
              <figcaption v-if="image.figcaption">
                {{ image.figcaption }}
              </figcaption>
            </figure>
          </TransitionGroup>
        </template>
      </div>
    </Transition>
  </div>
</template>

<style lang="scss" scoped>
  .image-galley-masonry-wrap {
    columns: v-bind(columns);
  }
  .image-galley-masonry-wrap {
    gap: v-bind(space);
    .image-gallery-masonry {
      &:not(:last-child) {
        margin-bottom: v-bind(space);
      }
    }
  }
  @media only screen and (max-width: 989px) {
    .image-galley-masonry-wrap {
      columns: v-bind(mdColumns);
    }
  }

  @media only screen and (max-width: 575px) {
    .image-galley-masonry-wrap {
      columns: v-bind(xsColumns);
    }
  }
</style>
