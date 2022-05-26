<script setup>
import Close from "./icons/close";

const openSingleImageBox = ref(false);
const openCloseSingleImageBox = () => openSingleImageBox.value = !openSingleImageBox.value;
const closeBackdrop = () => props.bgBackdropClose ? openSingleImageBox.value = !openSingleImageBox.value : null;

const single_image = ref(null);
const singleImageWidth = ref(null)
const singleImageHeight = ref(null)

const props = defineProps({
  imageUrl: {
    type: String,
    default: `https://picsum.photos/1280/720?random`,
    required: true
  },
  animation: {
    type: String,
    default: "fade",
    required: true
  },
  alt: {
    type: String
  },
  figcaption: {
    type: String
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
  }
})

onMounted (() => {
  singleImageWidth.value = single_image.value.clientWidth;
  singleImageHeight.value = single_image.value.clientHeight;
})
</script>
<template>
  <div class="single-image-wrap">
    <figure class="single-image" @click="openCloseSingleImageBox">
      <img
        :src="props.imageUrl"
        :alt="props.alt"
        class="image"
        :class="[
          {'is-rounded': props.isRounded },
          {'is-circled': props.isCircled },
          {'has-shadow': props.hasShadow }
        ]"
        loading="lazy"
        :width="singleImageWidth"
        :height="singleImageHeight"
        ref="single_image"
      >
    </figure>
    <Transition :name="props.animation" mode="out-in">
      <div class="single-image-prettybox" v-if="openSingleImageBox">
        <Transition name="backdrop" mode="out-in" appear>
          <div
            class="bg-backdrop"
            @click="closeBackdrop"
          ></div>
        </Transition>
        <button class="close-button" @click="openCloseSingleImageBox">
          <Close/>
        </button>
        <figure class="single-image">
          <img
            :src="props.imageUrl"
            :alt="props.alt"
            class="image"
            :class="[
              {'is-rounded': props.isRounded },
              {'is-circled': props.isCircled },
              {'has-shadow': props.hasShadow }
            ]"
            loading="lazy"
          >
          <figcaption v-if="props.figcaption">
            {{ props.figcaption }}
          </figcaption>
        </figure>
      </div>
    </Transition>
  </div>
</template>
