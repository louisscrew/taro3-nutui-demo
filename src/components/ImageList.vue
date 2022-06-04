<template>
  <view class="imagelist-container">
    <div
      class="image-item"
      v-for="(item, index) in imageSrc"
      :key="item"
      @click="doShowItem(item, index)"
    >
      <image class="image" mode="aspectFill" :src="item" />
    </div>

    <nut-imagepreview
      :show="showPreview"
      :images="imgData"
      @close="doHideFn"
    />
  </view>
</template>

<script>
import { reactive, toRefs, computed } from "vue"
export default {
  name: "ImageList",
  props: {
    imageSrc: {
      type: Array,
      default() {
        return []
      },
    },
  },
  setup(props) {
    let { imageSrc } = props
    let state = reactive({
      showPreview: false,
      initNo: 1,
    })
    const imgData = computed(() => {
      let r = []
      if (imageSrc && imageSrc.length > 0) {
        for (let img of imageSrc) {
          r.push({
            src: img,
          })
        }
      }
      return r
    })
    const doShowItem = (src, idx) => {
      // state.initNo = idx + 1
      state.showPreview = true
    }
    const doHideFn = () => {
      state.showPreview = false
    }
    return {
      ...toRefs(state),
      imgData,
      doHideFn,
      doShowItem,
    }
  },
}
</script>

<style lang="scss">
.imagelist-container {
  display: grid;
  grid-template-columns: 100px 100px 100px;
  grid-template-rows: 100px 100px 100px;
  grid-row-gap: 20px;
  grid-column-gap: 20px;
  align-items: center;
  justify-content: center;
  padding: 10px;

  .image-item {
    width: 100px;
    height: 100px;
    border: 2px solid rgb(167, 166, 166);
    border-radius: 5px;
    padding: 5px;
    .image {
      width: 100%;
      height: 100%;
    }
  }
}

// .nut-swiper-inner {
//   display: flex;
// }
// .nut-popup .nutui-popup__content-wrapper {
//   overflow: hidden;
// }
</style>
