<template>
  <div class="hello">
    <ul>
      <li v-for="item in goods" v-bind:key="item.id">
        <span>商品:{{item.text}}</span>
        <span>价格:{{item.price}}</span>
        <button @click="addCart(item)">加入购物车</button>
      </li>
    </ul>
    <input type="text" v-model="text">
    <button @click="addProduct">添加</button>
    <Cart ref="cart"></Cart>
  </div>
</template>

<script>
import Cart from './Cart'
export default {
  name: 'HelloWorld',
  data(){
    return {
      title:"",
      goods:[
        {id:1,text:'目录一',price:"666"},
        {id:2,text:'目录二',price:"555"},
        {id:3,text:'目录三',price:"111"},
        {id:4,text:'目录四',price:"3685"}
      ],
      text:""
    }
  },
  components: {
    Cart,
  },
  created(){
    setTimeout(() => {
      this.title = "定时器title"
    }, 3000);
  },
  methods:{
    addProduct(){
      if(this.text){
        this.goods.push({
          id:this.goods.length+1,
          text:this.text,
          price:"1356"
        })
      }
      this.text = "";
    },
    addCart(item){
      this.$refs.cart.addCart(item)
    }
  },
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul li {
  list-style:none;
}
a {
  color: #42b983;
}
</style>
