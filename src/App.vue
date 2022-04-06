<template>
  <p>hello this this vue</p>
  <button @click="count++">count is {{count}} </button>

  <pre><button @click="lang"> 浪起来 </button></pre>
  <button @click="stop"> 停止 </button>

  <p> {{msg}} </p>
</template>

<script>


export default {
  el: '#app',

  data(){
    return{
      msg: '猥琐发育， 别浪！',
      count: 999,
      internalID: null
        }
  },

  methods:{
    lang(){
      if(this.internalID != null)return;
      this.internalID = setInterval( ()=>{
      console.log(this.msg)
      var start = this.msg.substring(0,1)
      var end = this.msg.substring(1)
      this.msg = end + start
      },
      400)
    },
    stop(){
      clearInterval(this.internalID)
      this.internalID = null
    }

  }
}
</script>

<style>

</style>
