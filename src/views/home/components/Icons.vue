<template>
  <div class="icon-wrapper">
    <div class="icon-item-wrapper">
      <swiper class="swiper-wrapper">
        <swiper-slide v-for="(page,index) in pages" :key="index">
          <div class="icon-item" v-for="item in page" :key="item.id">
            <div class="icon-img-wrapper">
              <img :src="item.url" alt="">
            </div>
            <p>{{item.text}}</p>
          </div>
        </swiper-slide>
      </swiper>
    </div>
  </div>
</template>
<script>
export default {
  name: 'HomeIcons',
  data () {
    return {
      icons: [
        {
          id: '001',
          url: 'https://pic5.40017.cn/01/000/5f/30/rBANC1qozNqAb3vRAAAD_Qg-dt4234.png',
          text: '火车票'
        },
        {
          id: '002',
          url: 'https://pic5.40017.cn/02/001/5f/ab/rBLkCFqozNqAJqPYAAAFlYq1v7A413.png',
          text: '机票'
        },
        {
          id: '003',
          url: '//pic5.40017.cn/01/000/5f/a5/rBLkBVqozNqAGbVbAAADpuwJ0xY082.png',
          text: '酒店住宿'
        },
        {
          id: '004',
          url: '//pic5.40017.cn/02/001/5f/ab/rBLkCFqozNqAF4UUAAAFH-2jq70957.png',
          text: '景点门票'
        },
        {
          id: '005',
          url: 'https://pic5.40017.cn/01/000/5f/30/rBANC1qozNqAb3vRAAAD_Qg-dt4234.png',
          text: '火车票'
        },
        {
          id: '006',
          url: 'https://pic5.40017.cn/02/001/5f/ab/rBLkCFqozNqAJqPYAAAFlYq1v7A413.png',
          text: '机票'
        },
        {
          id: '007',
          url: '//pic5.40017.cn/01/000/5f/a5/rBLkBVqozNqAGbVbAAADpuwJ0xY082.png',
          text: '酒店住宿'
        },
        {
          id: '008',
          url: '//pic5.40017.cn/02/001/5f/ab/rBLkCFqozNqAF4UUAAAFH-2jq70957.png',
          text: '景点门票'
        },
        {
          id: '009',
          url: '//pic5.40017.cn/02/001/5f/ab/rBLkCFqozNqAF4UUAAAFH-2jq70957.png',
          text: '景点门票'
        }
      ]
    }
  },
  computed: {
    pages () {
      let pages = {}
      this.icons.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      console.log(pages)
      return pages
    }
  }
}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'
  .icon-wrapper
    width 100%
    height 0
    overflow hidden
    padding-bottom 40%
    position relative
    .icon-item-wrapper
      position absolute
      left 0
      top 0
      right 0
      bottom 0
      .icon-item
        float left
        width 25%
        height 50%
        overflow hidden
        position relative
        p
          position absolute
          bottom 0
          height .44rem
          line-height .44rem
          width 100%
          text-align center
          color $darkTextColor
        .icon-img-wrapper
          position absolute
          left 0
          right 0
          top .2rem
          bottom .44rem
          text-align center
          img{
            height 100%
            margin 0 auto
          }
</style>
