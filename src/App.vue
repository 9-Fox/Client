
<template>
  <div>
    <b-container class="bv-example-row mb-3">
<<<<<<< HEAD
        <b-row cols="2" align-h="around" v-if="!postselected">
=======
      <b-row cols="2" align-h="around">
>>>>>>> 5357e96935a62bb4e5da4c135b53e734195be9bd
        <b-button v-b-modal.modal-1>Launch demo modal</b-button>
        <b-modal id="modal-1" title="BootstrapVue">
          <UploadForm></UploadForm>
        </b-modal>
<<<<<<< HEAD
          <MainCard v-for="(item, key) in allpostlist" :key="key" :data="item" v-on:selectedPost="showPost($event)"></MainCard>
=======
        <!-- <MainCard v-for="(item, key) in sample" :key="key" :data="item"></MainCard> -->
>>>>>>> 5357e96935a62bb4e5da4c135b53e734195be9bd
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
<<<<<<< HEAD
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
=======
    UploadForm
  },
  data() {
    return {
      sample: [
        {
          title: "Daun",
          Like: 1,
          gambur:
            "https://image.shutterstock.com/image-photo/white-transparent-leaf-on-mirror-260nw-1029171697.jpg"
        },
        {
          title: "Anjing Lagi Lari, Ini Lucu ga??",
          Like: 5,
          gambur:
            "https://www.animatedimages.org/data/media/202/animated-dog-image-0175.gif"
        },
        {
          title: "Gatau Mau bikin Judul APa",
          Like: 12,
          gambur:
            "https://si.wsj.net/public/resources/images/JR-AA461B_IFVOL_P_20191031165108.jpg"
        },
        {
          title: "Entah apa ini",
          Like: 19,
          gambur:
            "https://www.animatedimages.org/data/media/140/animated-love-image-0187.gif"
        }
      ]
    };
  },
  methods: {
    printSample(payload) {
      console.log("masuk ga?");
      this.sample = payload;
>>>>>>> 5357e96935a62bb4e5da4c135b53e734195be9bd
    }
  },
}
</script>
    
<style scoped>
#maincard {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
</style>