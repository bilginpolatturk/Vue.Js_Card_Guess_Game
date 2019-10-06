<template>
    <div class="container">
        <h1> <b>  You Got The Correct Choice!!! Congratulations ! </b></h1>
        <button @click="newGame"> <b>Try Again ! <br> Have a Nice Luck !  </b> </button>
    </div>  
</template>
<script>
export default {
    methods : {
        newGame(){
        this.$emit("isActiveEvent","app-game-cards");
        }
    }
}
</script>
<style scoped>

 .container{
     position: absolute;
     top: 0px;
     left: 0px;
     width: 100%;
     height: 100%;
     display: flex;
     flex-direction: column;
     align-items: center;
     justify-content: center;
     
 }

 .container h1 {
     text-align: center;
     font-size: 300%;
     color: darkgreen;
     opacity: .8;
 }
 .container button{
     width: 300px;
     background-color: #fff;
     color: darkred;
     border: 1px solid darkgreen;
     height: 100px;
     font-size: 25px;
     border-radius: 5px;
     outline: none;
    transition: all .5s;
    cursor: pointer;
 }
 .container button:hover{
     background-color: darkgreen;
     color: #fff;
     transition: all .5s;

 }   
</style>