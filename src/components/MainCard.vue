<template>
  <div class="m-2">
    <h3>{{data.title}}</h3>
    <b-card
      overlay
      :img-src="data.image"
      img-alt="Card Image"
      text-variant="white"
      v-on:click="selectPost"
    ></b-card>
    <p>{{data.likes.length}} Like</p>
    <span class="spanduk h1 mb-2">
      <b-icon icon="heart-fill" variant="danger"></b-icon>
    </span>
    <span class="spanduk h1 mb-2">
      <b-icon icon="heart" variant="dark"></b-icon>
    </span>
    <span class="spanduk h1 mb-2">
      <b-icon icon="chat" variant="dark" v-on:click="selectPost"></b-icon>
    </span>
    <span class="spanduk h1 mb-2">
      <b-icon icon="cursor" variant="dark" @click="shareFB"></b-icon>
    </span>
    <Comment :data="postdata"></Comment>
  </div>
</template>

<script>
export default {
  name: "MainCard",
  props: ["data"],
  data() {
    return {};
  },
  created() {
    console.log(this.data);
  },
  methods: {
    selectPost() {
      this.$emit("selectedPost", this.data._id);
    },
    sending() {
      this.$emit("send-sample", this.sample);
      console.log(this.sample);
    },
    shareFB() {
      FB.ui(
        {
          method: "share",
          href: this.data.image
        },
        function(response) {}
      );
    }
  },
  props: ["data"]
};
</script>

<style scoped>
.spanduk {
  cursor: pointer;
}
</style>