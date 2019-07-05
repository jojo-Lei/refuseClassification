<template>
  <div  class= "container" @click="clickHandle">
    <div class="userinfo" @click = "toCitypage">{{cityName}}</div>

    <div class= "headSearch">
      <!-- <div class="headSearchInput" @click= "tosearch">
          <img class="search_image" src = "/static/images/icons/search.png"  alt="">
          <input class="headersearch" type="search" placeholder="搜素垃圾对应的分类项"> 
      </div> -->
      <mp-searchbar :isFocus=true :inputValue="inputValue" :placeholder="placeholder" 
      @input="input" @blur="blur" @focus="focus"></mp-searchbar>
      <!-- <img class="userinfo-avatar" v-if="userInfo.avatarUrl" :src="userInfo.avatarUrl" background-size="cover" /> -->

      <div class = "nav-left">
        <ul >
          <li v-for="(value,index) in object1" >
           {{value.title}}:{{value.shortIntro}}
            </br>{{value.requireList}}
          </li>
        </ul>
      </div>  

      <div class="item">
        <div @click="toDetail">跳转</div>
        </div>
      </div>
  </div>
   

</template>

<script>
import card from '@/components/card';
import sideBar from '@/components/sideBar';
import mpSearchbar from 'mpvue-weui/src/searchbar';
export default {
  data () {
    return {
      object1:[{
          // url:'/static/images/icons/add.png',
          title:'湿垃圾',
          shortIntro:'是指易腐蚀的生物质废弃物。主要包括剩菜剩饭、瓜皮果核、花卉绿植、肉类碎骨、过期食品、餐厨垃圾等。',
          requireList:[
            '纯流质的食品垃圾，如牛奶等。应直接倒进下水口',
            '有包装物的湿垃圾应将包装物取出后分类投放，包装物请投放到对应的可回收物容器或干垃圾容器',
            '投放湿垃圾时，鼓励将包装物（如塑料袋）去掉'
          ]},
          {
          title:'干垃圾',
          shortIntro:'是指除有害垃圾、可回收垃圾、湿垃圾以外的其他生活废弃物。',
          requireList:[
            '尽量沥干水分',
            '难以辨识类别的生活垃圾投入干垃圾容器内'
          ]},
          {
          title:'可回收',
          shortIntro:'是指适宜回收和可循环再利用的废弃物。主要包括废玻璃、废塑料、废纸张、废织物等。',
          requireList:[
            '轻投轻放',
            '清洁干燥，避免污染',
            '废纸尽量平整',
            '立体包装请清空内容物，清洁后压扁投放',
            '有尖锐边角的，应包裹后投放'
          ]},{
          title:'有害垃圾',
          shortIntro:'是指对人体健康或者自然环境造成直接或者潜在危害的零星废弃物，单位集中生产的除外。主要包括废电池、废灯管、废药品、废油漆等。',
          requireList:[
            '充电电池、纽扣电池、蓄力电池投放时请注意轻放',
            '油漆桶、杀虫剂如有残留请密封后投放',
            '荧光灯、节能灯易破损请连带包装或包裹后轻放',
            '废药品及其包装连带包装一并投放'
          ]}
      ]
    }
  },

  components: {
    card,
    mpSearchbar,
    sideBar,
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
      
    },
    toDetail(){
      console.log("22222222");
      wx.navigateTo({
          // url: "/page/counter/main?id=" + id
          url: "/pages/detail/main"
        });
    },
  },
  created () {
    // let app = getApp()
  }
}
</script>

<style scoped>
.headSearch{
  width: 100%;
}
.headSearchInput{
      width: 690rpx;
      display:flex;
      margin: 10px auto 20px;
      background: #fff;
      border-radius: 50rpx;
      font-size: 14px;
      overflow: hidden;
}
.headSeachISearch{
      padding: 20rpx 30rpx;
      caret-color: #c2c2c2
}
  
/* .item {
  display: flex;
  flex-direction: column;
  align-items: center;
} */

/* .search_image {
  width: 40rpx;
  height: 40rpx;
  margin: 15rpx;
  border-radius: 50%;
} */

img{
  width: 40rpx;
  height: 40rpx;
}

.userinfo-nickname {
  color: #aaa;
}

.usermotto {
  margin-top: 150px;
}

/* .search_image{
  display: inline-block;
} */

.form-control {
  display: block;
  /* padding: 0 12px; */
  margin-bottom: 5px;
  border: 1px solid #ccc;
}
.all{
  width:7.5rem;
  height:1rem;
  /* background-color:blue; */
}
.all:after{
  display:block;
  content:'';
  clear:both;
}
.left{
  float:left;
  width:3rem;
  height:1rem;
  background-color:red;
}

.right{
  float:left;
  width:4.5rem;
  height:1rem;
  background-color:green;
}
</style>
