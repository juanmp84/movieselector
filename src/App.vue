<script setup>
  import {ref, reactive} from 'vue'
  const peoples = reactive([
    {id: 1, name: 'Marianne Morales Cruz', selected: false},
    {id: 2, name: 'Jessy Cordero Garcia', selected: false},
    {id: 3, name: 'Alejandro Gomez Garcia', selected: false},
    {id: 4, name: 'Juan Miguel Perez Fauria', selected: false},
  ])

  const isLoading = ref(false)
  const isSelected = ref(false)

  const selectedPeople = ref({})

  const handleSubmit = () => {
    isLoading.value = true
     
    setTimeout( () => {
      selectedPeople.value = peoples[Math.floor(Math.random()*peoples.length)];
      isLoading.value = false      
    }, 1000)
  }
</script>

<template>
  <div style="margin-top: 15px;">
    <img src="./assets/youtube.png" alt="movie" width="250">

    <div v-if="isLoading" class="spinner" style="margin-top: 25px;"></div>


    <div class="peopleContainer">
      <ul v-if="!isSelected">
        <li v-for="(item, index) in peoples" :key="index" class="itemList">{{item.name}}</li>
      </ul>
    </div>

    <div style="margin-top: 50px;">
      <button class="selectButton" @click="handleSubmit">Click Here</button>
    </div>

    <div class="selected" v-if="selectedPeople.name">
      <p>Felicidades {{selectedPeople.name}} ganaste el sorteo</p>
    </div>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.selected {
  color: red;
  font-size: 25px;
  font-weight: bold;
  margin-top: 50px;
}

.peopleContainer {
  margin-top: 25px;
}

.peopleContainer ul li {
  list-style-type: none;
}

.itemList {
  color: blueviolet;
  font-weight: bold;
  margin-bottom: 5px;
  font-size: 20px;
}

.selectButton {
  background-color: #911881; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}

.spinner {
  margin: auto;
  width: 36px;
  height: 36px;
  border: 5px solid rgba(0, 0, 0, 0.3);
  border-radius: 50%;
  border-left-color: #7d47ff;

  animation: spin 1s ease infinite;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}



</style>
