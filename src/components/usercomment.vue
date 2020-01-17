<template>
    <b-row align-h="center" id="post">
        <b-col cols="1">
            <b-img v-bind="mainProps" rounded="circle" thumbnail fluid :src="data.user.profile" alt="Image 1"></b-img>
        </b-col>
        <b-col cols="4" align-self="center">
            <h4>{{ data.user.name }}</h4>
            <p>{{ data.description }}</p>
        </b-col>
    </b-row>
</template>

<script>
    export default {
    name: 'postcomments',
    props: ['data'],
    data(){
        return{
            mainProps: { blank: false, width: 75, height: 75, class: 'm1' }
        }
    }
    }
</script>

<style>
    #post{
        margin-bottom: 20px;
        position: sticky
    }

</style>