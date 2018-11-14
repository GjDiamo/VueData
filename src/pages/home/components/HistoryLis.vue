<template>
  <div>
    <!--&lt;!&ndash;声明式的跳转&ndash;&gt;
       <router-link tag="div" to="/detail?code=123">点击跳转</router-link>
       &lt;!&ndash;编程方式进行跳转&ndash;&gt;
       <button @click="goToDetail('/detail?code=456')">编程方式跳转</button>-->
    <history-item v-for="history in data" :key="history.code" :history="history">
      <!--这一步是遍历所有的信息；并且给遍历后的文件：起了个“history”名字；-->
      <!--后面的定义属性，目的是让本组件的的子组件接收我传过去的信息,并用props管道接收-->
      <!--@click.native="goToDetail('/detail?code='+history.code)"这个是跟组件原生跳转-->
    </history-item>
  </div>
</template>

<script>
  import HistoryItem from './HistoryItem'
  export default {
    name: "history-list",
    props:['data'],
    /*子组件通过这个props管道接收到属性：data，便可以获取到historyList里所有的内容；*/
    components:{
      HistoryItem
    },
  /*  methods: {
      goToDetail(path) {
        // /detail?code=123
        this.$router.push(path);
        // this.$router : 代表的全局的路由器
        // this.$route : 代表的是当前的路由信息
      }
    }*/
  }
</script>
<style scoped>
</style>
<!--
1，给vue组件绑定事件时候，必须加上native ，不然不会生效（监听根元素的原生事件，使用 .native 修饰符）
2，等同于在自组件中：
子组件内部处理click事件然后向外发送click事件：$emit("click".fn)-->
