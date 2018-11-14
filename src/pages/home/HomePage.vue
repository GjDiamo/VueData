<template>
    <div>
      <!--标题栏-->
      <title-bar :title="title" ></title-bar>

      <!--轮播图-->
      <carousel></carousel>

      <!--历史记录-->
      <!--在父组件里面定义一个data属性并且将historyList传递给子组件-->
      <history-list :data="historyList"></history-list>

      <!--底部菜单栏显示-->
      <menu-bar index="1"></menu-bar>
    </div>
</template>

<script>
    import TitleBar from '@/pages/common/TitleBar';
    import Carousel from '@/pages/common/Carousel';
    import HistoryList from '@/pages/home/components/HistoryLis';
    import MenuBar from '@/pages/common/MenuBar'
    import axios from 'axios'

    export default {
        name: "home-page",
        components:{
          TitleBar,
          Carousel,
          HistoryList,
          MenuBar
        },
        data(){
          return {
            title:'博彩首页',
            historyList:[]
            //这个是我们定义的根组件想要的信息；用一个historyList:[]来进行装载；
          }
        },
        mounted(){
          // http://localhost:80/api/index
          // http://localhost:3000/api/index
          axios.get('/api/index').then(resp=>{
            this.historyList = resp.data.data
            //发起请求,当数据请求回来的时候,我要将数据渲染到页面上
          });
        }
    }
</script>

<style scoped>

</style>
