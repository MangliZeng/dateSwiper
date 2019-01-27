<template>
  <md-popup
    v-model="isPopupShow"
    position="bottom"
  >
    <div class="md-example-popup md-example-popup-bottom">
      <swiper :options="swiperOption" ref="mySwiper">
        <!-- slides -->
        <swiper-slide v-for="(date, index, key) in listdate" :key="key">
          {{date.text | formatDate}}<br />
          {{date.text | formatDay}}
        </swiper-slide>
      </swiper>
    </div>
  </md-popup>
</template>

<script>
import { Popup } from 'mand-mobile'
import { format } from 'date-fns'
// import { zh } from 'date-fns/locale'
import { swiper, swiperSlide } from 'vue-awesome-swiper'

export default {
  name: 'dailog',
  props: {
    myShow: {
      type: Boolean,
      default: false
    }
  },
  data () {
    return {
      listdate: [
        {
          text: new Date(2014, 1, 11).getTime(),
          status: false
        },
        {
          text: new Date(2014, 1, 12).getTime(),
          status: true
        },
        {
          text: new Date(2014, 1, 13).getTime(),
          status: true
        },
        {
          text: new Date(2014, 1, 14).getTime(),
          status: false
        },
        {
          text: new Date(2014, 1, 15).getTime(),
          status: true
        },
        {
          text: new Date(2014, 1, 16).getTime(),
          status: true
        },
        {
          text: new Date(2014, 1, 17).getTime(),
          status: false
        },
        {
          text: new Date(2014, 1, 18).getTime(),
          status: true
        },
        {
          text: new Date(2014, 1, 19).getTime(),
          status: true
        },
        {
          text: new Date(2014, 1, 20).getTime(),
          status: false
        },
        {
          text: new Date(2014, 1, 21).getTime(),
          status: true
        }
      ],
      swiperOption: {
        slidesPerView: 5,
        spaceBetween: 30,
        slidesPerGroup: 5,
        loop: false,
        loopFillGroupWithBlank: false,
        observer: true,
        observeParents: true
      }
    }
  },
  filters: {
    formatDate (v) {
      let date
      switch (new Date(v).getDay()) {
        case 0: date = '日'
          break
        case 1: date = '一'
          break
        case 2: date = '二'
          break
        case 3: date = '三'
          break
        case 4: date = '四'
          break
        case 5: date = '五'
          break
        default: date = '六'
          break
      }
      return date
    },
    formatDay (v) {
      return format(v, 'DD')
    }
  },
  components: {
    [Popup.name]: Popup,
    swiper,
    swiperSlide
  },
  computed: {
    swiper () {
      return this.$refs.mySwiper.swiper
    },
    isPopupShow () {
      console.log('dailog', this.myShow)
      return this.myShow
    }
  },
  mounted () {
    // current swiper instance
    // 然后你就可以使用当前上下文内的swiper对象去做你想做的事了
    console.log('this is current swiper instance object', this.swiper)
    this.swiper.slideTo(3, 1000, false)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='stylus' scoped>
.dateBox
  display flex
  flex-flow row nowrap
  background-color #ffffff
  .item
    flex 1
    height 100px
    line-height 100px
.swiper-container {
  height: 200px;
  line-height 100px;
  width: 100%;
}
.swiper-slide {
  text-align: center;
  font-size: 38px;
  font-weight: 700;
  background-color: #eee;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
}
</style>
