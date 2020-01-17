<template>
  <b-container fluid style="margin-top: 20px;">
    <b-row align-h="center">
        <a :href="twitterImg" class="twitter-share-button" data-size="large" data-text="Share this with your friend!!" data-hashtags="9fox" data-show-count="false">Tweet</a>
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
    created(){
        console.log(this.data, 'ini apa')
        let postId = this.data._id
        axios({
            method: 'get',
            url: `http://localhost:3000/comments/${postId}`,
            headers: {
                token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjVlMjEwZmUzZDhkYWU0MGY1Njk1ODQ1ZSIsImlhdCI6MTU3OTIzNzA3M30.aKMVkoYAWW-9htyf9wlxtRiW2phEe3Gm6_1x9hFjhsk"
            }
        })
        .then(({data})=>{
            console.log(data)
            this.commentlist = data
        })
        .catch(err=>{
            console.log(err)
        })
    },
    data() {
        return {
            commentlist:[],
            postImage: this.data.image
        }
    },
    computed:{
        twitterImg(){
            return 'https://twitter.com/share?ref_src=' + this.postImage
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
                return axios({
                    method: 'get',
                    url: `http://localhost:3000/comments/${postId}`,
                    headers:{
                        token: ''
                    }
                })
            })
            .then(({data})=>{
                console.log(data)
                this.commentlist = data
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