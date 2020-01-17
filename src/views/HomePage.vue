
<template>
  <div>
    <b-container class="bv-example-row mb-3">
      <b-row cols="2" align-h="around" v-if="!postselected">
        <b-button v-b-modal.modal-1>Add Post</b-button>
        <b-modal id="modal-1" title="BootstrapVue" @ok="test">
          <div>
            <!-- <b-form @submit="onSubmit" @reset="onReset" v-if="show"> -->
            <b-form-input id="input-2" v-model="form.title" required placeholder="Enter Post Title"></b-form-input>
            <b-form-file @change="onFileChange" v-model="form.file" class="mt-3" plain></b-form-file>
            <b-img v-if="url" :src="url" fluid alt="Fluid image"></b-img>
            <!-- </b-form> -->
          </div>
        </b-modal>
        <MainCard
          v-for="(item, key) in allpostlist"
          :key="key"
          :data="item"
          v-on:selectedPost="showPost($event)"
        ></MainCard>
      </b-row>
      <b-row v-else>
        <button v-on:click="clearSelected">back</button>
        <MainCard :data="postselected"></MainCard>
        <Comment :data="postselected"></Comment>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Comment from "../components/comment";
import MainCard from "../components/MainCard";
import UploadForm from "../components/uploadForm";
export default {
  name: "HomePage",
  components: {
    MainCard,
    UploadForm,
    Comment
  },
  created() {
    axios({
      method: "get",
      url: "http://localhost:3000/posts"
    })
      .then(({ data }) => {
        this.allpostlist = data;
        // console.log(this.allpostlist)
      })
      .catch(err => {
        console.log(err);
      });
  },

  data() {
    return {
      allpostlist: [],
      postselected: null,
      form: {
        file: null,
        title: ""
      },
      url: ""
    };
  },

  methods: {
    clearSelected() {
      this.postselected = null;
    },
    showPost(id) {
      for (let i = 0; i < this.allpostlist.length; i++) {
        // console.log('masuk loop')
        let post = this.allpostlist[i];
        if (post._id == id) {
          this.postselected = post;
        }
      }
    },
    test() {
      let formData = new FormData()
      formData.append('title', this.form.title)
      formData.append('file', this.form.file)
      axios({
        method: "post",
        url: `http://localhost:3000/posts`,
        headers: {
          token:
            "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjVlMjEwZmUzZDhkYWU0MGY1Njk1ODQ1ZSIsImlhdCI6MTU3OTIzNzA3M30.aKMVkoYAWW-9htyf9wlxtRiW2phEe3Gm6_1x9hFjhsk"
        },
        data: formData
      })
        .then(({ data }) => {
          console.log(data, "post created");
          this.allpostlist.push(data)
        })
        .catch(err => {
          console.log(err);
        });
    },
    onFileChange(e) {
      const file = e.target.files[0];
      this.url = URL.createObjectURL(file);
    }
  }
};
</script>
    
<style scoped>
</style>