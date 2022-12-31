<template>
    <div class="card">
        <h2>{{moedaA}} para {{moedaB}}</h2>
        <!-- usar o v-bind para poder pegar o valor atribuido a moeadaA -->
        <!-- v-model é usado para pegar o valor digitado no campo de input e atribuir a variavel -->
        <input type="text" v-model="moedaA_value" v-bind:placeholder="moedaA"/> 
        <input type="button" value="Converter" v-on:click="convert"/>
        <h2>{{ moedaB_value }}</h2>
    </div>
</template>

<script>
export default {
    name: 'card',
    props: ["moedaA", "moedaB"],
    data(){
        return{
            moedaA_value: "",
            moedaB_value: 0
        }
    },
    methods: {
        convert() {
            let moedas = this.moedaA+"-"+this.moedaB
            let moedasCotacao = this.moedaA+this.moedaB

            let api = "http://economia.awesomeapi.com.br/json/last/"+moedas

            fetch(api, {})
            .then(res=>{return res.json()})
            .then(json=>{
                console.log(json)
                let cotacao = json[moedasCotacao].bid;
                this.moedaB_value = (cotacao * parseFloat(this.moedaA_value)).toFixed(2)
            });
        }
    }
}
</script>

<style>
.card {
    padding: 20px;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    margin: 40px;
}
</style>