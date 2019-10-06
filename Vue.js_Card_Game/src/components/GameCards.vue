<template>
    
    <div class="game-area">
        <h1 class="title"> Where is my<span> Card </span><strong>?</strong></h1>
        <h4 class="description"> Please select one card, then guess the match card</h4>
        <div class="container">
            <transition-group name="rotate-cards" appear class="card-container">
            <app-card 
            :key="card.id"
            :class="{'shadow' : selectedCard == card.id}" @click.native="selectedCard = card.id" v-for="card in cards" :card="card" >

            </app-card>

            </transition-group>
           
        </div>
        <div class="container">
            
                     <transition name="rotate" mode="out-in" >
                <component 
                :is="activeCard" @click.native="showCard(matchCard)"  :card="matchCard">
                
                </component>
            
            </transition>
      
           
            
        </div>
    </div>
</template>
<script>

import Card from './Card';
import DefaultCard from './DefaultCard';
export default {
    components : {
        appCard : Card,
        appDefaultCard : DefaultCard
    },
    data(){
        return {
            selectedCard : null,
            matchCard : {},
            activeCard : DefaultCard,
            cards : [
                {id : 1,component : "app-card",image : "/src/assets/card-1.jpg"},
                {id : 2,component : "app-card",image : "/src/assets/card-2.jpg"},
                {id : 3,component : "app-card",image : "/src/assets/card-3.jpg"},
                {id : 4,component : "app-card",image : "/src/assets/card-4.jpg"},
                {id : 5,component : "app-card",image : "/src/assets/card-5.jpg"},
                {id : 6,component : "app-card",image : "/src/assets/card-6.jpg"},
                
            ]
           
        }
    },
    created(){
        let matchCard = Math.floor(Math.random() * this.cards.length +1);
        this.matchCard = this.cards[matchCard-1];
        console.log(this.matchCard);
    },
    methods : {
        showCard(matchCard){
            if(this.selectedCard == null){
                alert("Please select one card");
            }else{
                this.activeCard = matchCard.component; // Card opening there

                setTimeout(() => {
                if(matchCard.id == this.selectedCard){
                   // alert("Correct choice!");
                   // this.choice = "Correct Choice";
                    this.$emit("isActiveEvent","app-celebrate");
                    
                }else{
                   // alert("Wrong choice")
                   // this.choice = "Wrong choice! Please retry the page and try again!";
                    this.$emit("isActiveEvent","app-failure");
                }


                },1200);
                
               
                
            }
          
        }
    }
}
</script>
<style scoped>
.title{
    text-align: center;
   
    color: pink;
}
.choice{
    text-align: center;
    color: maroon;
}

.title span{
    color: palevioletred;

}
.title strong{
    color: darkred;
}

.description{
    color: darkgrey;
    text-align: center;
}
.container, .card-container{
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 50px;
}
.shadow{
    box-shadow: 0px 5px 48px #30969f !important ;
    transition: box-shadow .5s;
}
/* Necessary Animations for cards */

.rotate-cards-enter{}
.rotate-cards-enter-active{
    animation: rotate-cards ease-in-out 2s forwards;
}
.rotate-cards-leave{}
.rotate-cards-leave-active{}



.rotate-enter{}
.rotate-enter-active{
animation: rotate-in ease-in-out .5s forwards;

}
.rotate-leave{}
.rotate-leave-active{
animation: rotate-out ease-in-out .5s forwards;    
}

@keyframes rotate-in {
    from{
        transform: rotateY(90deg);
    }
    to{
        transform: rotateY(0deg);
    }
}
@keyframes rotate-out {
    from{
        transform: rotateY(0deg);
    }
    to{
        transform: rotateY(90deg);
    }
}
@keyframes rotate-inback {
    from{
        transform: rotateY(90deg);
    }
    to{
        transform: rotateY(180deg);
    }
}
@keyframes rotate-outback {
    from{
        transform: rotateY(180deg);
    }
    to{
        transform: rotateY(90deg);
    }
}
@keyframes rotate-cards {
    from{
        transform: rotateY(0);
    }
    to{
        transform: rotateY(1800deg);

    }
}

/* End of card animation */

</style>