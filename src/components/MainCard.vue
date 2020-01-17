<template>
  <div class="m-2">
      <h3>Name</h3>
    <b-card
      overlay
      :img-src="gambur"
      img-alt="Card Image"
      text-variant="white"
    ></b-card>
    <span class="spanduk h1 mb-2 ">
      <b-icon icon="alert-circle-fill" variant="success"></b-icon>
    </span>
    <span class="spanduk h1 mb-2">
      <b-icon icon="alert-circle-fill" variant="success"></b-icon>
    </span>
    <span class="spanduk h1 mb-2">
      <b-icon icon="alert-circle-fill" variant="success"></b-icon>
    </span>
  </div>
</template>

<script>
export default {
  nmae: "MainCard",
  data() {
    return {
      sample: "This is a sample text",
      gambur: "https://image.shutterstock.com/image-photo/white-transparent-leaf-on-mirror-260nw-1029171697.jpg"
    };
  },
  methods: {
      sending(){
          this.$emit('send-sample', this.sample)
          console.log(this.sample)
      }
  }
};
</script>

<style scoped>
.spanduk {
  cursor: pointer;
}
</style>