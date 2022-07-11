<template class="template">
    <h1 class="ask-title">{{ ask }}</h1>
    <div class="res-container">
       <img :src="img" alt="respuesta">
       <div class="res-title">{{getAnwerTranslate}}</div>
    </div>

    <input class="ask-input" v-model="ask" type="text" placeholder="Escribe una pregunta...">
</template>

<script>
export default {
    data(){
        return {
            ask:'',
            answer:'',
            img:null||'https://media3.giphy.com/media/xUOxfjsW9fWPqEWouI/200w.webp?cid=dda24d507fb6f379a91ee69a15d11567ffb0484c465940ab&rid=200w.webp&ct=g'
        }
    },
    methods:{
        async getAnswer(){

            try {
                const data = await fetch('https://yesno.wtf/api').then(r=>r.json());
                this.img = data.image;
                this.answer = data.answer;
            } catch (error) {
                console.error(error);
            }

        }
    },
    computed:{
        getAnwerTranslate: function(){
            return this.answer=='yes'?'Sí':this.answer=='no'?'No':this.answer=='maybe'?'Talvez':'';
        }
    },  
    watch:{
        ask( value, oldValue){
            if(!value.length){
                this.img = 'https://media3.giphy.com/media/xUOxfjsW9fWPqEWouI/200w.webp?cid=dda24d507fb6f379a91ee69a15d11567ffb0484c465940ab&rid=200w.webp&ct=g';
                this.answer = '';
            }else{
                if( !value.includes('?')){ return }
                this.getAnswer();    
            }
        }
            
    }
}
</script>

<style >
    .ask-title{
        margin: 20px;
    }
    .res-container{
        width:90%;
        max-width: 800px;
        height:320px;
        margin: 0 auto;
        position: relative;
        border-radius: 20px;
        overflow: hidden;
        box-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
    }
    .res-container img{
        width:100%;
        height:100%;
        object-fit: cover;
        filter: brightness(70%);
        /* position: relative; */
    }
    .res-container .res-title{
        display: flex;
        align-items: center;
        justify-content: center;
        width:100%;
        height: 100%;
        position:absolute;
        top: 0;
        font-weight: bold;
        font-size: 1.8rem;
        color: aliceblue;
    }

    .ask-input{
        width: 90%;
        max-width: 800px;
        margin: 20px 0;
        height:40px;
        padding:0 15px;
        border-radius: 5px;
        border: none;
        outline: none;
        font-size:1rem;
        box-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
    }

    @media only screen and (min-width: 768px)  {
        .res-container{
            height:500px
        }
    }
</style>
