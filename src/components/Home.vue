

<template>
    <h1>Home</h1>
    <div class="container">
        <div class="item" v-for="data in myJson">
            <div class="img"></div>
            <div class="data">
                <div>Name :  {{data["name"]}}</div>
                <div>Location :  {{data["location"]["city"]}} {{data["location"]["address"]}}</div>
            </div>
        </div>
    </div>
</template>

<script>

import json from '../json/hotels.json'

      export default{
          data(){
              return{
                  myJson: json
              }
          }
      }
</script>

<style scoped>

.container{
    display: flex;
    flex-flow : row wrap;
}

.item{
    display: flex;
    flex-flow : row wrap;
    padding: 7px;
    margin: 5px;
    background: rgb(86, 86, 86);
    text-color:white;
    color: white;
}

.img{
    height: 50px;
    width: 50px;
    background: grey;
    margin-right: 15px;
}

.data{
    display: flex;
    flex-flow : column nowrap;
}

</style>