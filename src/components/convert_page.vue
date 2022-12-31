<template>
  <div class="page">
    <h1>Conversor de Moedas</h1>
    <div class="line">
      <card moedaA="BRL" moedaB="USD"/>
      <card moedaA="USD" moedaB="BRL"/>
    </div>
    <div class="line">
      <card moedaA="BRL" moedaB="EUR"/>
      <card moedaA="EUR" moedaB="BRL"/>
    </div>
    <div class="line">
      <card moedaA="BRL" moedaB="ARS"/>
      <card moedaA="ARS" moedaB="BRL"/>
    </div>
  </div>
</template>

<script>
import card from "./convert_card.vue"
export default{
  name: "ConvertPage",
  components:{
    card
  }
}
</script>

<style scoped>
.page {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.line {
  display: flex;
  flex-direction: row;
}
</style>