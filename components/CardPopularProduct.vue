<template>
  <div v-if="showSlice" class="w-full mb-4 md:mb-0 padding-card md:px-6 rounded-lg bg-lightgrey">
    <div class="">
      <div class="mb-heading gutter lg:mx-8 justify-center">
        <img :src="image.url" :alt="image.alt" class="h-[200px] lg:h-60 w-full max-w-md object-cover rounded-lg" />
      </div>
      <div class="gutter">
        <h4 class="mb-2 text-teal typo-h-highlight lg:typo-h-highlight-desktop">
          {{ $prismic.asText(highlighted) }}
        </h4>
        <h3 class="mb-heading typo-h-sm lg:typo-h-sm-desktop">
          {{ $prismic.asText(heading) }}
        </h3>
        <RichText :data="text" />
        <div class="flex justify-end">
          <Button :label="linkLabel" :link="link" :btnType="btnType" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    data: {
      type: Object,
      required: false,
      default() {
        return {}
      },
    },
  },
  computed: {
    heading() {
      return this.data?.heading
    },
    text() {
      return this.data?.text
    },
    highlighted() {
      return this.data?.highlighted_heading
    },
    image() {
      return this.data?.image
    },
    color() {
      return this.data?.background_color
    },
    linkLabel() {
      return this.data?.link_label
    },
    link() {
      return this.data?.link
    },
    btnType() {
      return this.data?.button_type
    },
    showSlice() {
      return Object.keys(this.image).length !== 0
    },
  },
}
</script>
