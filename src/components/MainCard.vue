<template>
  <div class="m-2">
      <h3>{{data.title}}</h3>
    <b-card
      overlay
      :img-src="data.gambur"
      img-alt="Card Image"
      text-variant="white"
    ></b-card>
    <p>{{data.Like}} Like</p>
    <span class="spanduk h1 mb-2 ">
      <b-icon icon="heart-fill" variant="danger"></b-icon>
    </span>
    <span class="spanduk h1 mb-2">
      <b-icon icon="heart" variant="dark"></b-icon>
    </span>
    <span class="spanduk h1 mb-2">
      <b-icon icon="chat" variant="dark"></b-icon>
    </span>
    <span class="spanduk h1 mb-2">
      <b-icon icon="cursor" variant="dark"></b-icon>
    </span>
    <Comment :data="postdata"></Comment>
  </div>
</template>

<script>
export default {
  nmae: "MainCard",
  data() {
    return {
      postdata: null,
      sample: "This is a sample text",
      gambur: "https://storage.googleapis.com/ninefox-data/1579229484627-Screenshot from 2019-11-21 16-15-23.png"
    };
  },
  methods: {
    clickCard(){
      axios({
        method: 'get',
        url: url
      })
      .then(({data})=>{
        this.postdata = data
      })
    },
      sending(){
          this.$emit('send-sample', this.sample)
          console.log(this.sample)
      }
  },
  props:['data']
};
</script>

<style scoped>
.spanduk {
  cursor: pointer;
}
</style>