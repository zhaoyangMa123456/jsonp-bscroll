<template>
  <div class="recommend">
    <div v-if="sliderList.length">
      <slider >
        <div v-for="item in sliderList" >
          <img class="needsclick" :src="item.picUrl">
        </div>
      </slider>
    </div>
  </div>
</template>
<script>
  import {getSliderList} from '../../api/recommend'
  import {ERR_OK} from '../../api/config'
  import Slider from '../slider/slider.vue'
  export default {
    name: 'recommend',
    data () {
      return {
        sliderList: []
      }
    },
    created () {
      this._initSlider()
    },
    methods: {
      _initSlider () {
        getSliderList().then((res) => {
          if (res.code === ERR_OK) {
            this.sliderList = res.data.slider
          }
        })
      }
    },
    components: {
      Slider
    }
  }
</script>
