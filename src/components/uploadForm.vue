<template>
  <div>
    <!-- <b-form @submit="onSubmit" @reset="onReset" v-if="show"> -->
    <b-form-input id="input-2" v-model="form.title" required placeholder="Enter Post Title"></b-form-input>
    <b-form-file @change="onFileChange" v-model="form.file" class="mt-3" plain></b-form-file>
    <b-img v-if="url" :src="url" fluid alt="Fluid image"></b-img>
    <!-- </b-form> -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        file: null,
        title: ""
      },
      url: ""
    };
  },
  methods: {
    onFileChange(e) {
      const file = e.target.files[0];
      this.url = URL.createObjectURL(file)
    },
    
  }
};
</script>

<style>
</style>