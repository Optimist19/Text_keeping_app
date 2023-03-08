<template>
  <main>
    <div class="overlay" v-if="vueLogo">
      <div class="modal">
        <textarea v-model.trim="note" ></textarea>
        <p v-if="show">{{show}}</p>
        <button @click="add">Add Note</button>
        <button @click="close" class="close">Close</button>
      </div>
    </div>
    <div class="container">
      <header>
        <!-- {{cards}} -->
        <h1>Notes</h1>
        <i @click="vueLogoShow" class="fa-brands fa-vuejs"></i>
      </header>
      <div class="cards-container">
        <div class="card" v-for="card in cards" :key="card.id" :style="{backgroundColor: card.backgroundColor}">
          <p class="main-text">
            {{card}}
          </p>
          <p class="date">{{card.date}}</p>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import {ref} from "vue"

export default {
  name: 'NoteCard',
  setup(){
    const vueLogo = ref(false)
    const note = ref("")
    const show = ref("")
    const cards = ref([])
    const currentDate = ref(new Date().toJSON().slice(0, 10))

    function vueLogoShow(){
      vueLogo.value = !false
    }

    function close(){
      vueLogo.value = false
    }

    function randomHsl() {
      return "hsl(" + Math.random() * 360 + ", 100%, 75%,)";
    }

    function add(){
      if(note.value.length <= 10){
        return show.value = "Text has to be 10 or more characters"
      }
      cards.value.push({
        id: Math.floor(Math.random() * 1000000),
        date: currentDate,
        text: note.value,
        backgroundColor: randomHsl(),
      })
      
      vueLogo.value = false,
      note.value =""
      // return(
      //   vueLogo.value = false,
      //   note.value = ""
      // )
    }

    return{
      vueLogo,
      vueLogoShow,
      close,
      note,
      cards,
      currentDate,
      randomHsl,
      add,
      show
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
main{
  height: 100vh;
  width: 100vw;
}

.container{
  max-width: 1000px;
  padding: 10px;
  margin: 0 auto;
}

header{
  display: flex;
  justify-content: space-around;
  align-items: center;
}

h1{
  font-size: 50px;
  font-weight: bold;
  margin-bottom: 25px;
}

i{
  font-size: 50px;
  cursor: pointer;
  color: rgb(97, 150, 128);
}

.card{
  width: 225px;
  height: 225px;
  background-color: rgb(247, 182, 44);
  padding: 10px;
  border-radius: 15px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin: 0 20px 20px 0;
}

.date{
  font-weight: bold;
  font-size: 12.5px;
}

.cards-container{
  display: flex;
  flex-wrap: wrap;
}

.overlay{
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.77);
  z-index: 10;
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal{
  width: 750px;
  background-color: white;
  padding: 30px;
  /* position: relative; */
  display: flex;
  flex-direction: column;
}

button{
  padding: 10px 20px;
  font-size: 20px;
  width: 100%;
  background-color: blueviolet;
  color: white;
  border: none;
  margin-top: 15px;
  cursor: pointer;
}

.close{
  background-color: red;
}
</style>
