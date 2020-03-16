<template lang="pug">
  .app
    //p.sebas(v-if="isName") sdfsdf
    div.sebas(@click="getDatos") Traer datos Corrona virus todos
    div(v-for="cases in covidCases")
      h3 Casos {{ cases.cases }}
      p Muertes {{ cases.deaths }}
      p Curadoss {{cases.recovered}}
    div.sebas(@click="getPais") Traer datos Corrona Virus por pais
    div(v-for="casos in covidPais")
      p Pais: {{ casos.country }} Casos: {{ casos.cases }} Casos de hoy: {{ casos.todayCases }} Muertes: {{casos.deaths}} Muertes Hoy: {{casos.todayDeaths}} Currados: {{casos.recovered}} Activos: {{casos.active}} Criticos: {{casos.critical}}
    //div(@click="changeMsg") {{ msg }}
    //div(v-for="day in week") {{ day }}
</template>

<script>
const axios = require("axios").default;
export default {
  name: "app",

  data() {
    return {
      msg: "Welcome to Your Vue.js App",
      isName: false,
      covidCases:[],
      covidPais:[]
    };
  },

  methods: {
    changeMsg() {
      this.msg = "que te tomas y tan";
      this.isName = true;
    },
    async getDatos() {
      const response = await axios.get('https://coronavirus-19-api.herokuapp.com/all')
          this.covidCases = [response.data]
          console.log(response)
    },
    async getPais(){
      const response = await axios.get('https://coronavirus-19-api.herokuapp.com/countries')
        this.covidPais = response.data
        console.log(response)

    }
  }
};
</script>

<style lang="stylus">
.app {
  text-align center
}

.sebas 
  color blue
  background-color red
  border-radius 30px
  text-align center
  display inline-block
  padding 30px
  cursor pointer
.sebas:hover
  background-color green
</style>
