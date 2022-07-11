<template>
  <h2>{{ customCounter }}</h2>
  <p>{{ counter }} <sup>2</sup> = {{squareCounter}}</p>

    <div>
        <button v-on:click="()=>incrementCounter(-1)" class="primary-button">-1</button>
        <button @click="()=>incrementCounter(1)" class="primary-button">+1</button>
    </div>

</template>

<script>
export default{
    props:{
        title:String,
        start:Number
    },
    data(){
        return{
            counter: this.start | 1
        }
    },
    methods:{
        getSquareValue(){
            return this.counter*this.counter;
        },
        incrementCounter(num){
            console.log('se ejecuta');
            this.counter = this.counter + num;
        }

    },
    computed:{ //se guarda en cache, solo cuando cambia se ejecuta de nuevo
        squareCounter(){
             return this.counter*this.counter;
        },
        customCounter(){
            return this.title || 'Counter'
        }
    }
}
</script>

<style>
    .primary-button{
        background-color:#EFEF9C;
        border-radius:3px;
        border:none;
        padding:9px 12px;
        margin: 5px;
    }
</style>