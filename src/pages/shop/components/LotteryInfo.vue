<template>
  <div class="row" style="margin-top: 10px;margin-bottom: 10px;" v-if="history.prizegrades[0]!=null">
    <div class="col-xs-4" style="padding-left: 0;">第{{history.code}}期</div>
    <div class="col-xs-8" style="padding-left: 0;padding-right: 0;" >
      奖池<span style="color: red;">{{history.poolmoney}}</span>,
      可开出<span style="color: red;" >{{history.prizegrades[0].typenum}}注</span>
      <Span>
        {{history.prizegrades[0].typemoney}}
      </Span>
    </div>
  </div>
</template>

<script>
   import axios from 'axios'
    export default {
        name: "lottery-info",
      data(){
          return{
            code: this.$route.query.code,

            history: {
              //页面初始化想要的数据，即prizegrades数组
              prizegrades:[]
            }
        }
      },
      mounted() {
        //发送请求获取 获取当前期的数据
        axios.get('/api/detail?code=' + this.code).then(resp => {
          this.history = resp.data.data;
          //边获取数据，边进行渲染到页面
          console.log(this.history.prizegrades)
        });
      }
    }
</script>

<style scoped>

</style>
