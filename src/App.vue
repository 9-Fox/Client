
<template>
<<<<<<< HEAD
  <div id="comment-section">
      <Comment :data="postData"></Comment>
=======
  <div >
    <b-container class="bv-example-row mb-3">
      <b-row cols="2" align-h="around">
          <MainCard></MainCard>
          <MainCard></MainCard>
          <MainCard></MainCard>
          <MainCard></MainCard>
          <MainCard></MainCard>
      </b-row>
      <b-row></b-row>
    </b-container>
>>>>>>> tampilannya udah
  </div>
</template>

<script>
<<<<<<< HEAD
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
=======
import MainCard from "./components/MainCard";
export default {
  name: "App",
  components: {
    MainCard
  },
  data(){
    return {
      sample: 'ch'
    }
  },
  methods:{
    printSample(payload){
      console.log('masuk ga?')
      this.sample = payload
    }
  }
};
>>>>>>> tampilannya udah
</script>
    
<style scoped>
#maincard {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
</style>>