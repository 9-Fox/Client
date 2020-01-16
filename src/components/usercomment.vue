<template>
    <b-row align-h="center">
        <b-col cols="1">
            <b-img v-bind="mainProps" rounded="circle" thumbnail fluid src="https://picsum.photos/250/250/?image=54" alt="Image 1"></b-img>
        </b-col>
        <b-col cols="1" align-self="center">
            <p >Username</p>
            <p>=========comments==========</p>
        </b-col>
    </b-row>
</template>

<script>
    export default {
    name: 'postcomments',
    data(){
        return{
            mainProps: { blank: false, width: 75, height: 75, class: 'm1' }
        }
    }
    }
</script>

<style>

</style>