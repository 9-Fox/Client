<template>
  <b-row align-h="center">
            <b-card bg-variant="dark" text-variant="white" img-src="https://placekitten.com/1000/300" img-alt="Card image" img-bottom id="card" style="padding:3px; border-radius: 10px;">
                <b-row align-h="left">
                    <b-col cols="2">
                        <b-img v-bind="mainProps" rounded="circle" thumbnail fluid src="https://picsum.photos/250/250/?image=54" alt="Image 1"></b-img>
                    </b-col>
                    <b-col cols="2">
                        <h4>{{ data.username}}</h4> 
                    </b-col>
                </b-row>
                <b-row align-h="center">
                    <b-col cols="12">
                        <p style="text-align:left;margin-bottom:0px;margin-top:10px">{{ data.caption }}</p>
                    </b-col> 
                </b-row>
            </b-card>
      </b-row>
</template>

<script>
export default {
    name: 'post',
    props:['data'],
    data(){
        return{
            mainProps: { blank: false, width: 75, height: 75, class: 'm1' }
        }
    }
}
</script>

<style>

</style>