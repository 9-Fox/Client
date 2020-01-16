<template>
  <b-row align-h="center">
            <b-col cols="1">
                <b-img v-bind="mainProps" rounded="circle" thumbnail fluid src="https://picsum.photos/250/250/?image=54" alt="Image 1"></b-img>
            </b-col>
            <b-col cols="4">
                <b-form-textarea
                    id="textarea"
                    v-model="text"
                    placeholder="Enter something..."
                    rows="3"
                    max-rows="6"
                    >
                </b-form-textarea>
            </b-col>
            <b-button>Post</b-button>
        </b-row>
</template>

<script>
    export default {
    name: 'postcomment'
    }
</script>

<style>

</style>