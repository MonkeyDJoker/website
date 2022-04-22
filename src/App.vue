<template>
  <p>hello this this vue</p>
  <button @click="count++">count is {{count}} </button>

  <pre><button @click="lang"> 浪起来 </button></pre>
  <button @click="stop"> 停止 </button>

  <p> {{msg}} </p>



<div class="panel panel-primary">

  <div class="panel-heading">
    <h3 class="panel-title">Add Brand</h3>
  </div>

  <div class="panel-body form-inline">
    <label>
      ID:
      <input type="text" class="form-control" v-model="id">
    </label>
    
    <label>
      Name:
      <input type="text" class="form-control" v-model="name">
    </label>

    <input type="button" value="ADD" class="btn btn-primary" @click="add()">
  </div>
</div>


<table>

<thead>
  <tr>
    <th>ID</th>
    <th>Name</th>
    <th>CreateTime</th>
    <th>Operation</th>
  </tr>

</thead>
<tbody>
<tr v-for="item in list" :key = "item.id">

  <td>{{item.id}} </td>

  <td v-text="item.name"></td>

  <td>{{item.date}} </td>
  
  <td>
    <a href="" @click.prevent="del(item.id)">Delete</a>
  </td>


</tr>

</tbody>

</table>
  
</template>

<script>


export default {
  el: '#app',

  data(){
    return{
      msg: '猥琐发育， 别浪！',
      count: 999,
      internalID: null,
      id:'',
      name:'',

      list:[
        {id:1,name: 'james',date: new Date()},
        {id:2,name: 'tony', date: new Date()}

      ]
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
    },

    //删除数据方法一 根据id找到索引后 运用some()的for循环 删除数据
    del(id){
      console.log(id)
      this.list.some((item,i)=>{
        if(item.id == id){
          this.list.splice(i,1)
          return true;
        }
      }
      )
    },

    //删除数据方法二 用list里的findindex方法 直接找到相应的item
    del_second(id){
      var index = this.list.findIndex(item =>{
        if(item.id == id){
          return true;
        }
      })

      console.log(index)
      this.list.splice(index,1)
    },
    //添加数据，每一次添加 要把ID和name清零
    add(){
      var car = { id: this.id, name: this.name,date: new Date()}
      this.list.push(car)
      this.id = this.name = ''
    }

  }
}
</script>

<style>

</style>
