<script setup>
import ListHome from '../components/ListHome.vue'
</script>

<template>
    <div class="main">

        <div class="top">
            <div class="search">
                <h1>Search</h1>
            </div>
        </div>


        <div class="bottom">
            <div class="filter">
                <h1>Filter</h1>
            </div>
            <div class="list">
                <ListHome/>
            </div>
        </div>

    </div>
</template>
    

<style scoped>
@use base;
@use container;

.main{
    display: flex;
    flex-flow: column nowrap;
    /* justify-content: center; */
    align-items: center;
}

.top{
    background-image:url("http://localhost:3000/basicImages/homeSearch.png");
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
    height: 30em;
    width: 90%;
}

.bottom{
    display: flex;
    flex-flow: row nowrap;
    width: 90%;
}

.filter{
    width: 40%;
    background-color: brown;
}

.list{
    width: 60%;
}

</style>

