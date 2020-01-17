<template>
  <b-container fluid style="margin-top: 20px;">
    <b-row align-h="center">
        <b-button variant="outline-primary" style="margin-top:10px;">Share to Twitter</b-button>
    </b-row>
    <hr class="my-4">
    <postcomment v-on:uploadcomment="userComment($event)"></postcomment>
    <hr class="my-4">
    <usercomments v-for="(item, index) in commentlist" :key="index" :data="item"></usercomments>
  </b-container>
</template>

<script>
import postcomment from './postcomment'
import usercomments from './usercomment'
export default {
    name: 'commentpage',
    components: {
        usercomments,
        postcomment
    },
    props: ['data'],
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
        userComment(payload){
            let postId = this.data._id
            axios({
                method: 'post',
                url: `http://localhost:3000/comments/${postId}`,
                headers: {
                    token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjVlMjEwZmUzZDhkYWU0MGY1Njk1ODQ1ZSIsImlhdCI6MTU3OTIzNzA3M30.aKMVkoYAWW-9htyf9wlxtRiW2phEe3Gm6_1x9hFjhsk"
                },
                data:{
                    description: payload
                }
            })
            .then(({data})=>{
                console.log(data, 'comment created')
            })
            .catch(err=>{
                console.log(err)
            })
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