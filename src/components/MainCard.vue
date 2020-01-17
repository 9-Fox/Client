<template>
  <div class="m-2">
      <h3>{{data.title}}</h3>
    <b-card
      overlay
      :img-src="data.image"
      img-alt="Card Image"
      text-variant="white"
      v-on:click="selectPost"></b-card>
      
    <span class="spanduk h1 mb-2 ">
      <b-icon icon="heart-fill" variant="danger" v-on:click="addLike"></b-icon>
      <span style="font-size: 15px">{{data.likes.length}} Like</span>
    </span>
    <span class="spanduk h1 mb-2">
      <b-icon icon="heart" variant="dark" v-on:click="addDislike"></b-icon>
      <span style="font-size: 15px">{{data.dislikes.length}} Dislike</span>
    </span>
    <span class="spanduk h1 mb-2">
      <b-icon icon="chat" variant="dark" v-on:click="selectPost"></b-icon>
    </span>
    <span class="spanduk h1 mb-2">
      <b-icon icon="cursor" variant="dark"></b-icon>
    </span>
    <!-- <Comment :data="postdata"></Comment> -->
  </div>
</template>

<script>
export default {
  name: "MainCard",
  props: ['data'],
  data() {
    return {
      likes:[],
      dislikes:[]
    };
  },
  created(){
    this.likes = this.data.likes
    this.dislikes = this.data.dislikes
  },
  methods: {
      addLike(){
        // console.log('masuk add likes')
        axios({
          method: 'patch',
          url: `http://localhost:3000/posts/likes/${this.data._id}`,
          headers:{
            token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjVlMjEwZmUzZDhkYWU0MGY1Njk1ODQ1ZSIsImlhdCI6MTU3OTIzNzA3M30.aKMVkoYAWW-9htyf9wlxtRiW2phEe3Gm6_1x9hFjhsk'
          }
        })
        .then(({data})=>{
          this.likes.push(data[data.length-1])
          // console.log(data,'ini yang muncul')
        })
        .catch(err=>{
          console.log(err)
        })
      },
      addDislike(){
        // console.log('masuk add dislikes')
        axios({
          method: 'patch',
          url: `http://localhost:3000/posts/dislikes/${this.data._id}`,
          headers:{
            token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjVlMjEwZmUzZDhkYWU0MGY1Njk1ODQ1ZSIsImlhdCI6MTU3OTIzNzA3M30.aKMVkoYAWW-9htyf9wlxtRiW2phEe3Gm6_1x9hFjhsk'
          }
        })
        .then(({data})=>{
          this.dislikes.push(data[data.length-1])
        })
        .catch(err=>{
          console.log(err)
        })
      },
      selectPost(){
        // console.log(this.data,'cuman satu')
        this.$emit('selectedPost', this.data._id)
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