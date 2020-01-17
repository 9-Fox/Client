<template>
  <b-container fluid style="margin-top: 20px;">
    <post :data="user"></post>
    <b-row align-h="center">
        <b-button variant="outline-primary" style="margin-top:10px;">Share to Twitter</b-button>
    </b-row>
    <hr class="my-4">
    <postcomment v-on:upload="userComment($event)" :data="user"></postcomment>
    <hr class="my-4">
    <usercomments v-for="(item, index) in commentlist" :key="index" :data="item"></usercomments>
  </b-container>
</template>

<script>
import post from './post'
import postcomment from './postcomment'
import usercomments from './usercomment'
export default {
    name: 'commentpage',
    components: {
        usercomments,
        postcomment,
        post
    },
    data() {
        return {
            commentlist:[
                {id: 1,name: 'serafim', comment:'lalalalalalla'},
                {id: 2,name: 'samuel', comment: 'aku sangat bahagia hari ini'},
                {id: 3,name: 'patra', comment: 'triliililililliliili'},
                {id: 4,name: 'samuel', comment: 'aku sangat bahagia hari ini'},
                {id: 5,name: 'patra', comment: 'triliililililliliili'},
                {id: 2,name: 'samuel', comment: 'aku sangat bahagia hari ini'},
                {id: 3,name: 'patra', comment: 'triliililililliliili'}
                ],
            usercomment: '',//ngetest aja
            user: {
                id: 1,
                username: 'serafim',
                caption: 'hehehehehe lucu banget',
                userpicture: 'picture',
                usermeme: 'meme'
                }
        }
    },
    methods:{
        userComment(v){
            this.usercomment = v
            //BERHASIL EMIT
            console.log(this.usercomment)
        }
    }
}
</script>

<style>
    #formcomment{
        width: 50vw;
    }
    #card{
        width: 50vw;
    }
</style>