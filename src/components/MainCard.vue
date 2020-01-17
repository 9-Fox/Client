<template>
  <div class="m-2" v-on:click="selectPost">
      <h3>{{data.title}}</h3>
    <b-card
      overlay
      :img-src="data.image"
      img-alt="Card Image"
      text-variant="white"
    ></b-card>
    <p>{{data.likes}} Like</p>
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
  </div>
</template>

<script>
export default {
  name: "MainCard",
  props: ['data'],
  data() {
    return {
    };
  },
  created(){
    console.log(this.data)
  },
  methods: {
      selectPost(){
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