<template>
    <div class="container">
        <div class="item" v-for="data in myJson">
        <div class="item2" v-for="info in data['rooms']">
            <div class="img">Img</div>
            <div class="data">
                <div>Name :  {{data["name"]}}</div>
                <div>Location :  {{data["location"]["city"]}} {{data["location"]["address"]}}</div>
                <div>Price : {{ info["price"] }}</div>
                <div>Area : {{ info["area"] }}</div>
            </div>
        </div>
        </div> 
    </div>
</template>

<script>

import { VueElement } from 'vue';
import json from '../json/hotels.json'
//import FromPicker from './components/FormPicker.vue'


export default{
          data(){
              return{
                  myJson: json,  
                //   picker: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
                //   picker2: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
                }
            }
}

</script>

<style scoped>
.container{
    display: flex;
    flex-flow : column nowrap;
    align-items: center;
    background-color: blue;
}
.item{
    width: 60%;
}
.item2{
    display: flex;
    flex-flow : row wrap;
    padding: 7px;
    margin: 5px;
    background: rgb(86, 86, 86);
    color: white;
}

.img{
    display: flex;
    height: 50px;
    width: 50px;
    background: grey;
    margin-right: 15px;
    align-items: center;
    justify-content: center;
}

.data{
    display: flex;
    flex-flow : column nowrap;
}
</style>