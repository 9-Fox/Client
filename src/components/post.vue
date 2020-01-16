<template>
  <b-row align-h="center">
            <b-card img-src="https://placekitten.com/1000/300" img-alt="Card image" img-bottom id="card">
                <b-row>
                    <b-col cols="2">
                        <b-img v-bind="mainProps" rounded="circle" thumbnail fluid src="https://picsum.photos/250/250/?image=54" alt="Image 1"></b-img>
                    </b-col>
                    <b-col cols="2">
                        <p>Username</p> 
                    </b-col>
                </b-row>
                <b-row align-h="center">
                    <b-col cols="12">
                        <p style="text-align:center;">disini captionnya dari user</p>
                    </b-col> 
                </b-row>
            </b-card>
      </b-row>
</template>

<script>
export default {
    name: 'post',
    data(){
        return{
            mainProps: { blank: false, width: 75, height: 75, class: 'm1' }
        }
    }
}
</script>

<style>

</style>