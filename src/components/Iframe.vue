<template>
  <div>
    <div id="from-bar">
      <h1>Input text here</h1>
      <br>
      <form action method="post">
          <input type="text" placeholder="Text 1" v-model="text0"/>
          <input type="text" placeholder="Text 2" v-model="text1"/>
          <input type="text" placeholder="Text 3" v-model="text2"/>
      </form>
    </div>
    <h6 style="text-align:center">After input text, choose your meme to generate meme</h6>
    <h5 style="margin: auto; text-align:center;">Choose your meme :</h5>
    <div id="boxer">
      <div class="warap">
        <div v-for="(item, index) in memeList" :key="index" class="boxy">
          <b-card :img-src="item.url" img-alt="Image" img-top class="mb-2">
            <b-button @click.prevent="createMeme(item.id)" variant="primary">Use this</b-button>
          </b-card>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Swal from "sweetalert2";
export default {
  name: "Iframe",
  data() {
    return {
      memeList: [],
      text0: "",
      text1: "",
      text2: "",
    };
  },
  methods: {
    createMeme(memeId) {
      console.log(memeId);
      // console.log(text1,text2,text0);
      axios
        .post("https://api.imgflip.com/caption_image", {
          data: {
            username: "artapnanayad",
            password: "pepepetoto",
            template_id: memeId,
            text0: this.text0,
            text1: this.text1,
            text2: this.text2
          },
          header:{"Access-Control-Allow-Origin" : "http://localhost:8080"}
        })
        .then(({ data }) => {
          console.log(data);
          Swal.fire("Success", `image link: ${data.data.url}`, "success");
          this.text0 = "";
          this.text1 = "";
          this.text2 = "";
        })
        .catch(err => {
          console.log(err);
          if (err.responseJSON.message) Swal(err.responseJSON.message);
          else Swal(err.responseJSON);
        });
    },
  },
  beforeMount() {
    axios
      .get("https://api.imgflip.com/get_memes")
      .then(({ data }) => {
        this.memeList = data.data.memes;
      })
      .catch(err => {
        console.log(err);
        if (err.responseJSON.message) Swal(err.responseJSON.message);
        else Swal(err.responseJSON);
      });
  }
};
</script>

<style scoped>
.warap {
  width: 100%;
  height: 700vh;
  display: flex;
  flex-flow: column wrap;
  background-color: whitesmoke;
  align-items: center;
}

.boxy {
  width: 150px;
  /* height: 150px; */
  margin: 10px;
}

#boxer {
  width: 100vw;
  max-width: 100vw;
  height: 60vh;
  max-height: 70vh;
  background-color: bisque;
}

#from-bar {
  width: 100vw;
  height: 30vh;
  margin: auto;
  padding: auto;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

* {
  overflow-x: hidden;
}
</style>