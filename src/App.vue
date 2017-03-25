<template>
  <div id="app">
<h1>{{title}}</h1>
<h1>{{hintmessage}}</h1>
<input v-model='newItem' v-on:keyup.enter="addNew">
<ul>
  <li v-for='item in items' v-bind:class="{finished:item.isFinished}" v-on:click="toolge(item)">{{item.label}}</li>
</ul>
<!-- <BuzhengVue msgFromFather="hello buzheng" v-on:child-tell-me-something='listenToMyBoy'></BuzhengVue>
<h1>{{childWords}}</h1> -->
  </div>
</template>

<script>
import Store from './store'
import BuzhengVue from './components/buzheng'
export default {
data:function (){
  return {
    title:'this is a todo list',
    hintmessage:'please enter the to do list',
    items:Store.fetch(),
    newItem:'',
    childWords:''
  }
},
components:{BuzhengVue},
methods:{
  toolge:function(item){
    item.isFinished=!item.isFinished
  },
  addNew:function(){
    this.items.push({
      label:this.newItem,
      isFinished:false
    })
    this.newItem=''
  },
  listenToMyBoy:function(msg){
    this.childWords=msg
  },
},
watch:{
  items:{
    handler:function(items){
      Store.save(items)
    },
    deep:true
  }
}
}
</script>

<style>
.finished{
  text-decoration: line-through;
}
</style>
