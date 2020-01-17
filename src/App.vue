
<template>
    <Iframe></Iframe>
  <!-- <div id="comment-section">
      <Comment :data="postData"></Comment>
  <div >
    <b-container class="bv-example-row mb-3">
      <b-row cols="2" align-h="around">
          <MainCard v-for="(item, key) in sample" :key="key" :data="item"></MainCard>
      </b-row>
      <b-row></b-row>
    </b-container>
  </div>
  </div> -->
</template>

<script>
import Comment from "./components/comment"
import MainCard from "./components/MainCard";
import Iframe from './components/Iframe';

export default {
  name: "App",
  components: {
    MainCard,
    Iframe
  },
  data(){
    return {
      sample: [
        {
        title: 'Daun',
        Like: 1,
      gambur: "https://image.shutterstock.com/image-photo/white-transparent-leaf-on-mirror-260nw-1029171697.jpg"

        },
        {
        title: 'Anjing Lagi Lari, Ini Lucu ga??',
        Like: 5,
      gambur: "https://www.animatedimages.org/data/media/202/animated-dog-image-0175.gif"
        },
        {
        title: 'Gatau Mau bikin Judul APa',
        Like: 12,
        gambur: "https://si.wsj.net/public/resources/images/JR-AA461B_IFVOL_P_20191031165108.jpg"

        },
        {
        title: 'Entah apa ini',
        Like: 19,
      gambur: "https://www.animatedimages.org/data/media/140/animated-love-image-0187.gif"

        }
      ]
    }
  },
  methods:{
    printSample(payload){
      console.log('masuk ga?')
      this.sample = payload
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