<template>
  <div class="icons">
    <swiper :options="swiperOption" >
      <swiper-slide v-for="(page,index) of pages" :key="index">
    <div class="icon" v-for="item of page" :key="item.id">
      <div class="icon-img">
      <img class="icon-img-content" :src="item.imgUrl" >
      </div>
      <p class="icon-desc">{{item.desc}}</p>
    </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        autoplay: false
      }
    }
  },
  // data () {
  //   return {
  //     iconList: [{
  //       id: '0001',
  //       imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
  //       desc: '景点门票'
  //     }, {
  //       id: '0002',
  //       imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/8c/47630407f70e8302.png',
  //       desc: '影视基地'
  //     }, {
  //       id: '0003',
  //       imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png',
  //       desc: '宁波必游'
  //     }, {
  //       id: '0004',
  //       imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/ab/6f7d6e44963c9302.png',
  //       desc: '泡温泉'
  //     }, {
  //       id: '0005',
  //       imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png',
  //       desc: '一日游'
  //     }, {
  //       id: '0006',
  //       imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/8c/47630407f70e8302.png',
  //       desc: '横店影视城'
  //     }, {
  //       id: '0007',
  //       imgUrl: 'http://img1.qunarzz.com/piao/fusion/1805/57/1e29afd06f881102.png',
  //       desc: '普陀山'
  //     }, {
  //       id: '0008',
  //       imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/b8/c5dcdb58deec2402.png',
  //       desc: '象山影视城'
  //     }, {
  //       id: '0009',
  //       imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/20/831d62d2e1c7be02.png',
  //       desc: '打卡圣地'
  //     }, {
  //       id: '0010',
  //       imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/80/416c6ab3368d1f02.png',
  //       desc: '全部玩乐'
  //     }]
  //   }
  // },
  computed: {
    pages () {
      const pages = []
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  @import "~styles/mixins.styl"
  .icons >>> .swiper-container
    height 0
    padding-bottom 50%
 .icons
   margin-top .1rem
   .icon
      position relative
      overflow hidden
      float left
      width 25%
      height 0
      padding-bottom 25%
   .icon-img
      position absolute
      top 0
      left 0
      right 0
      bottom .44rem
      box-sizing border-box
      padding .1rem
   .icon-img-content
      display block
      margin 0 auto
      height 100%
   .icon-desc
      position absolute
      left 0
      right 0
      bottom 0
      height .44rem
      line-height .44rem
      color $darkTextColor
      text-align center
      ellipsis()
</style>
