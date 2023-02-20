<script>
  export default {
    data() {//
      return {
        inputText: '',//initiella värdet är tomt
        savedInputs: [],//värderna sparas i en array
        showList: true,//listan syns som standarvärde
      }
    },
    methods: {
        saveInput() {
        this.savedInputs.push(this.inputText);//används för att lägga till värden i listan
        this.inputText = '';
      },
      toggleList() {//funktionen för att visa/dölja listan med värden
        this.showList = !this.showList;
      }
    },
    components: {
        ChildComponent: {
            props: {
                inputData: {//prop
                    type: Array,
                    required: true,
                },
            },
            template: '<div><ul><li v-for="item in inputData" :key="item">{{ item }}</li></ul></div>',
        }
    }
  }
</script>
<template>
<div>
    <form @submit.prevent="saveInput"><!--form med input och submitknapp-->
        <input v-model="inputText"  placeholder="Skriv något här..."><!--V-model-->
        <button>Submit</button>
    </form>
    <button @click="toggleList">Visa/Göm lista</button><!--en knapp som visar/gömmer listan med input värderna-->
    <ul v-if="showList">
        <li v-for="item in savedInputs" :key="item">{{ item }}</li><!--for loop som renderar varje element i savedInputs-->
    </ul>
    <child-component :inputData="savedInputs"></child-component><!--komponent som tar emot en prop som innehåller savedInputs-->
  </div>
</template>
<style>

</style>
