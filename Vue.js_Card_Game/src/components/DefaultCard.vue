<template>
     <div class="card">
           
            </div>
</template>,
<script>
export default {
    
}
</script>
<style scoped>
.card{
    width: 200px;
    height: 232px;
    border-radius: 5px;
    border: 1px solid #666;
    background-color: purple;

    /* margin-left: 15px; */
    background-image: url("../assets/vue-bg.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    box-shadow: 0px 9px 55px #666;
    
}
.card:hover{
    box-shadow: 0px 5px 48px #666;
    transition: box-shadow .5s;


}
.card img{
    width: 100%;
    height: 100%;
}
</style>