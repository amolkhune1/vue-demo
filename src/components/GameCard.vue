<template>
<table>
    <tbody>
        <tr :key="index"  class="margin" v-for="(cardTitle,index) in cardsArray">
            <td  v-on:click="changeText(index)"  >
                {{ cardTitle }}
            </td>
        </tr>
    </tbody>
</table>
</template>
<script>
export default{
    name:'CardsComponent',
    data(){
        return{
            cardTitle:'down',
            cardsArray:[],
            otherTitle:'up',
            previousIndex:null
        }
    },
    created:function(){
    this.calculateCards();
   },
    props:{
        amount:String,
    },
    methods:{
        calculateCards(){
            for(let i=0;i<this.amount;i++){
                this.cardsArray.push(this.cardTitle);
            }
        },
        changeText(index){
            if(this.cardsArray[index]==this.cardTitle){
                if(this.previousIndex!=null){
                    this.cardsArray[this.previousIndex]=this.cardTitle;
                }
                this.cardsArray[index]=this.otherTitle;
                this.previousIndex=index;
            }
            console.log(this.cardsArray);
        }
    }
}
</script>
<style>
.margin{
    margin: 20px;
    border: 1px solid;
}
</style>