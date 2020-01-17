
<template>
    <b-container class="bv-example-row mb-3">
      <b-row cols="2" align-h="around" v-if="!postselected">
          <MainCard v-for="(item, key) in allpostlist" :key="key" :data="item" v-on:selectedPost="showPost($event)"></MainCard>
      </b-row>
      <b-row v-else>
          <button v-on:click="clearSelected">back</button>
          <MainCard :data="postselected"></MainCard>
          <Comment :data="postselected"></Comment>
      </b-row>
    </b-container>
</template>

<script>
import Comment from "./components/comment"
import MainCard from "./components/MainCard";
export default {
  name: "App",
  components: {
    MainCard,
    Comment
  },
  created(){
    axios({
      method: 'get',
      url: 'http://localhost:3000/posts'
    })
    .then(({data})=>{
      this.allpostlist = data
      // console.log(this.allpostlist)
    })
    .catch(err=>{
      console.log(err)
    })
  },
  data(){
    return {
      allpostlist: [],
      postselected: null
    }
  },
  methods:{
    clearSelected(){
      this.postselected = null
    },
    showPost(id){
      for(let i =0; i<this.allpostlist.length; i++){
        // console.log('masuk loop')
        let post = this.allpostlist[i]
        if(post._id == id){
          this.postselected = post
        }
      }
    }
  }
};
</script>
    
<style scoped>
#maincard {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
</style>