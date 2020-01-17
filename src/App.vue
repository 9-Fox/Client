<template>
  <div id="comment-section">
      <Comment :data="postData"></Comment>
  </div>
</template>

<script>
import Comment from "./components/comment"
export default {
name: "App",
components:{
    Comment
},
data(){
  return{
    postData: ''
  }
},
methods:{
  onclickCard(){
    //axio
    // this.postData = //data yang diambil
  }
}
}
</script>

<style>

</style>