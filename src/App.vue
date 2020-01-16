
<template>
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
  </div>
</template>

<script>
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
</script>
    
<style scoped>
#maincard {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
</style>>