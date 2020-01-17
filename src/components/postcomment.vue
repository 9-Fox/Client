<template>
  <b-row align-h="center" sticky-header :items="items">
            <b-col cols="1">
                <b-img v-bind="mainProps" rounded="circle" thumbnail fluid src="https://picsum.photos/250/250/?image=54" alt="Image 1"></b-img>
            </b-col>
            <b-col cols="4">
                <b-form-textarea
                    id="textarea"
                    placeholder="Enter something..."
                    rows="3"
                    max-rows="6"
                    v-model="comment"
                    >
                </b-form-textarea>
            </b-col>
            <b-button v-on:click="uploadPost">Post</b-button>
        </b-row>
</template>

<script>
    export default {
    name: 'postcomment',
    props:["data"],
    data(){
        return{
            comment: '',
            mainProps: { blank: false, width: 75, height: 75, class: 'm1' }
        }
    },
    methods:{
        uploadPost(){
            this.$emit('upload', this.comment)
        }
    }
}
</script>

<style>

</style>