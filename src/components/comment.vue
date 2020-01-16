<template>
  <b-container fluid style="margin-top: 20px;">
    <post></post>
    <b-row align-h="center">
        <b-button variant="outline-primary">Share to Twitter</b-button>
    </b-row>
    <hr class="my-4">
    <postcomment></postcomment>
    <hr class="my-4">
    <usercomments></usercomments>
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