<template>
  <div>
    <table border="1">
      <thead>
        <tr>
          <th>课程名</th>
          <th>单价</th>
          <th>数量</th>
          <th>价格</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="c in cart" :key="c.id">
          <td>{{c.text}}</td>
          <td>{{c.price}}</td>
          <td>{{c.count}}</td>
          <td>{{c.price*c.count}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  data () {
    return {
        cart:[]
    };
  },
  methods:{
    addCart(item){
      const ret = this.cart.find(v => v.id === item.id);
      if(ret){
        ret.count += 1;
      }else{
        this.cart.push({...item,count:1})
      }
    }
  }
}

</script>
<style lang="stylus" rel="stylesheet/stylus">
</style>