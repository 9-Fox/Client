
<template>
  <div>
    <b-container class="bv-example-row mb-3">
        <b-row cols="2" align-h="around" v-if="!postselected">
        <b-button v-b-modal.modal-1>Launch demo modal</b-button>
        <b-modal id="modal-1" title="BootstrapVue">
          <UploadForm></UploadForm>
        </b-modal>
          <MainCard v-for="(item, key) in allpostlist" :key="key" :data="item" v-on:selectedPost="showPost($event)"></MainCard>
      </b-row>
      <b-row v-else>
          <button v-on:click="clearSelected">back</button>
          <MainCard :data="postselected"></MainCard>
          <Comment :data="postselected"></Comment>
    </b-container>
  </div>
</template>

<script>
import Comment from "./components/comment";
import MainCard from "./components/MainCard";
import UploadForm from "./components/uploadForm";
export default {
  name: "App",
  components: {
    MainCard,
    UploadForm,
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

  data() {
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
  },
}
</script>
    
<style scoped>
</style>