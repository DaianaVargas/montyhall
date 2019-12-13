<template>
    <div id="app">
        <h1>Problema de Monty Hall</h1>
        <div class="form">
            <div v-if="!started">
                <label for="doorsAmount">Quantas portas?</label>
                <input type="text" id="doorsAmount" size="3"
                    v-model.number="doorsAmount">
            </div>
            <div v-if="!started">
                <label for="selectedDoor">Qual é a porta premiada?</label>
                <input type="text" id="selectedDoor" size="3"
                    v-model.number="selectedDoor">
            </div>
            <button v-if="!started" @click="started=true">Iniciar</button>
            <button v-if="started" @click="started=false">Reiniciar</button>
        </div>
        <div class="doors" v-if="started">
            <div v-for="i in doorsAmount" :key="i">
                <Door :hasGift="i === selectedDoor" :number="i"/>
            </div>
        </div>
        <!-- <Door number="1" :hasGift="true"/> -->
    </div>
</template>

<script>
import Door from './components/Door'

export default {
  name: 'App',
  components: { Door },
  data () {
    return {
      started: false,
      doorsAmount: 3,
      selectedDoor: null
    }
  }
}
</script>

<style>
* {
    box-sizing: border-box;
    font-family: 'Montserrat', sans-serif;
}

body {
    color: #fff;
    background: linear-gradient(to right, rgb(21,153,87), rgb(21,87,153) );
}

#app {
    display: flex;
    flex-direction: column;
    align-items: center;
}

#app h1 {
    border: 1px solid #000;
    background-color: #0004;
    padding: 20px;
    margin-bottom: 60px;
}

.form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 40px;
}

.form {
    margin-bottom: 10px;
    font-size: 2rem;
}

.form input {
    margin-left: 10px;
    margin-bottom: 10px;
    font-size: 24px;
}

.form button {
    height: 60px;
    width: 140px;
    border-color: #000;
    background-color: #0004;
    /* background-color: #ffdb4d; */
    margin-bottom: 10px;
    padding: 10px;
    font-size: 20px;
    font-weight: bold;
    color: #fff;
}

.doors {
    align-self: stretch;
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
}

</style>
