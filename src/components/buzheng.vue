<template lang="html">
  <div id="buzheng">
<h1>{{title}}</h1>
<button v-on:click="getMessageFromFather">getMessageFromFather</button>
  </div>
</template>

<script>
export default {
  data:function(){
    return{
      title:'hello',
        message:'from child tells'
    }
  },
  props:["msgFromFather"],
  methods:{
    getMessageFromFather:function(){
        console.log(this.message)
        this.$emit('child-tell-me-something',this.message)
    }

  }
}
</script>

<style lang="css">
</style>
