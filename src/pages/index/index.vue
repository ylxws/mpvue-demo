<template>
  <div @click="clickHandle" class="home">
    <div class="banner">
      <swiper class="swiper" indicator-dots="true" autoplay="true" interval="500000" duration="100000">
          <block v-for="(item, index) in movies" :index="index" :key="index">
              <swiper-item>
                  <image :src="item.url" class="slide-image" mode="aspectFill"/>
              </swiper-item>
          </block>
      </swiper>
    </div>
    <div class="types">
      <div class="types-item" v-for="item in types" :key="item.key">
        <div class="img">
          <img src="https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2244227252,3703055936&fm=26&gp=0.jpg">
        </div>
        <p>{{item.name}}</p>
      </div>
    </div>
    <div class="hot box">
      <div class="title">热销推荐</div>
      <div class="hot-item" v-for="item in hots" :key="item.id">
        <div class="hot-img">
          <img src="https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2244227252,3703055936&fm=26&gp=0.jpg">
          <!-- <img :src="item.img" alt=""> -->
        </div>
        <div class="hot-right">
          <!-- <p class="hot-title">马油护手霜{{item.title}}</p>
          <p class="hot-des">好用马油护手霜大家撒扩大接哦二五是滴哦</p>
          <p class="hot-price">
            <span class="newPrice">￥49</span>
            <span>￥90</span>
          </p> -->
          <p class="hot-title">{{item.title}}</p>
          <p class="hot-des">{{item.des}}</p>
          <p class="hot-price">
            <span class="newPrice">￥{{item.price}}</span>
            <span>￥{{item.oldPrice}}</span>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      types:[
        {name: '肠胃', key: 1},
        {name: '肠胃', key: 2},
        {name: '肠胃', key: 3},
        {name: '肠胃', key: 4},
        {name: '肠胃', key: 5},
        {name: '肠胃', key: 6},
        {name: '肠胃', key: 7},
        {name: '肠胃', key: 8},
        {name: '肠胃', key: 9},
        {name: '肠胃', key: 10}
      ],
      hots: [
        {
          id: 1,
          // img: require('https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=1180637067,725005331&fm=26&gp=0.jpg'),
          title: '马油护手霜',
          des: '好用马油护手霜大家撒扩大接哦二五是滴哦',
          price: 49,
          oldPrice: 90
        },
        {
          id: 2,
          // img: require('https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=1180637067,725005331&fm=26&gp=0.jpg'),
          title: '马油护手霜',
          des: '好用马油护手霜大家撒扩大接哦二五是滴哦',
          price: 49,
          oldPrice: 90
        },
        {
          id: 3,
          // img: require('https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=1180637067,725005331&fm=26&gp=0.jpg'),
          title: '马油护手霜',
          des: '好用马油护手霜大家撒扩大接哦二五是滴哦',
          price: 49,
          oldPrice: 90
        }
      ],
      motto: 'Hello miniprograme',
      userInfo: {
        nickName: 'mpvue',
        avatarUrl: 'http://mpvue.com/assets/logo.png'
      },
      movies: [
        {
          url: 'https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=1121052022,1090121728&fm=26&gp=0.jpg'
        },
        {
          url: 'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=2372471715,1706020394&fm=26&gp=0.jpg'
        }
      ]
    }
  },

  components: {
    card
  },

  methods: {
    bindViewTap () {
      const url = '../logs/main'
      if (mpvuePlatform === 'wx') {
        mpvue.switchTab({ url })
      } else {
        mpvue.navigateTo({ url })
      }
    },
    clickHandle (ev) {
      console.log('clickHandle:', ev)
      // throw {message: 'custom test'}
    }
  },

  created () {
    // let app = getApp()
  }
}
</script>

<style scoped>
  .gift-item{
    border: 1px solid red;
    width: 30%;
  }
  .gift-img{
    width: 30%;
  }
  .gift-img img{
    width: 100%;
  }
  .home{
    padding: 10px;
  }
  .banner{
    margin: 5px;
  }
  .swiper{
    width: 100%;
    margin-bottom:15px;
  }
  .slide-image{
    width: 100%;
  }
  .types{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    align-items: center
  }
  .types-item{
    width: 18%;
    overflow: hidden;
    margin-bottom: 10px;
  }
  .types-item .img{
    width: 60px;
    height: 60px;
    display: inline-block;
    border-radius: 50%;
    overflow:hidden;
  }
  .types-item .img img{
    width: 100%;
    height: 100%;
  }
  .types-item p{
    text-align: center;
    font-size: 12px;
  }
  .box{
    box-shadow: #ccc 0px 0px 2px 1px;
  }
  .hot{
    margin-top: 20px;
  }
  .title{
    color: red;
    font-size: 16px;
    padding: 15px;
  }
  .hot-item{
    display: flex;
    padding: 15px;
  }
  .hot-img{
    width: 60px;
    height: 60px;
  }
  .hot-img img{
    width: 100%;
    height: 100%;
  }
  .hot-right{
    flex: 1;
    margin-left: 20px;
  }
  .hot-title{
    font-size: 14px;
    font-weight: bolder;
  }
  .hot-des{
    font-size: 12px;
    color: #999;
  }
  .hot-price span{
    color: #999;
    font-size: 12px;
    margin-right: 10px;
  }
  .hot-price .newPrice{
    color: red;
    font-size: 14px;
  }
</style>
