<template>
  <view class="index">
    <ImageList :imageSrc="imageSrc"></ImageList>
    <nut-button type="primary">主要按钮</nut-button>
  </view>
</template>

<script>
import { reactive, toRefs } from "vue"
import ImageList from "../../components/ImageList.vue"
export default {
  name: "Index",
  components: {
    ImageList,
  },
  setup() {
    const state = reactive({
      imageSrc: [
        "https://img2.baidu.com/it/u=2941204833,2269914636&fm=253&fmt=auto&app=138&f=JPEG?w=1083&h=500",
        "https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fc-ssl.duitang.com%2Fuploads%2Fblog%2F202008%2F27%2F20200827010326_5990c.thumb.1000_0.jpg&refer=http%3A%2F%2Fc-ssl.duitang.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656941303&t=890e25e581443c9916436343219c61d6",
        "https://gimg2.baidu.com/image_search/src=http%3A%2F%2Finews.gtimg.com%2Fnewsapp_match%2F0%2F12056677512%2F0.jpg&refer=http%3A%2F%2Finews.gtimg.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656941303&t=653ec376dd0777799a3f8a27e51188c4",
      ],
    })

    return {
      ...toRefs(state),
    }
  },
}
</script>

<style lang="scss">
.index {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
