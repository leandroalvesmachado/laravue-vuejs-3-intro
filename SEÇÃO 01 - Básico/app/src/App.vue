<template>
  <div>
    <TheHeader v-if="showHeader" />

    <div v-show="showName">
        Nome: {{ firstName }} <br>
        Sobrenome: {{ lastName }}
    </div>

    <div v-if="accessLevel === 'admin'">Usuário Admin</div>
    <div v-else-if="accessLevel === 'marketing'">Usuário Marketing</div>
    <div v-else>Usuário normal</div>

    <div
      v-for="obj in todos"
      v-bind:key="obj.id"
    >
      {{ obj.title }}
    </div>

    <br>
    
    <!-- v-bind indica que vai receber um valor dinamico, variavel -->
    <div
      v-for="(obj, index) in todos"
      v-bind:key="obj.id"
    >
      <img
        v-if="obj.imgSrc"
        :src="obj.imgSrc"
      >
      {{ index }} - {{ obj.title }}
    </div>

    <h1 :class="classVar">
      Curso Vue 3
    </h1>

    <!-- aplica a classe caso seja true -->
    <h1 :class="{ 'title': true, 'title-home': isHome }">
      Curso Vue 3
    </h1>

    <!-- Two-way data binding -->
    <div>
      <div>
        Two-way data binding
      </div>
      <input v-model="name" type="text">
      <br>
      {{ name }}
      <br>
      <label for="">Sports</label>
      <select v-model="sports">
        <option value="">Escolha</option>
        <option value="futebol">Futebol</option>
        <option value="skate">Skate</option>
      </select>
      <br>
      {{ sports }}

      <br>
      <label for="">Newsletter</label>
      <input v-model="newsletter" type="radio" value="Sim"> Sim
      <input v-model="newsletter" type="radio" value="Não"> Não
      <br>
      {{ newsletter }}
    </div>

    <br><br>

    <div>
        <label>Contrato</label> <br>
        <input
            v-model="contract"
            type="checkbox"
        > Aceita nosso termos... <br>

          {{ contract }}
    </div>

    <br><br>

    <div>
        <label>Cores que você mais gosta</label> <br>
        <input
            v-model="colors"
            type="checkbox"
            value="Azul"
        > Azul

        <input
            v-model="colors"
            type="checkbox"
            value="Amarelo"
        > Amarelo <br>
          {{ colors }}
    </div>

    <br><br>
    <!-- Eventos -->

    <div>
      <!-- v-on = capture o evento que for definido -->
      <!-- v-on:click = capturando o evento click do botão -->
      <!-- v-on = @ forma reduzida -->
      <button v-on:click="onClick">Enviar</button>
      <button @click="onClick()">Enviar</button>
    </div>

    <div @mouseover="onMouseOver()">MouseOver</div>

    <!-- modificadores de eventos = @submit.prevent, altera o comportamento padrão -->
    <!-- @keyup.enter = evento acionado quando a tecla enter é presionada -->
    <form
      action="https://google.com"
      @submit.prevent="onSubmit"
    >
      <input
        type="text"
        @keyup.enter="onKeyUp"
      >
      <button type="submit">
        Enviar
      </button>
    </form>

    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TheHeader from './components/TheHeader.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    TheHeader
  },
  data() {
    return {
      showHeader: true,
      firstName: 'Jon',
      lastName: 'Snow',
      showName: false,
      accessLevel: 'admin',
      classVar: 'title',
      isHome: true,
      name: 'Jon snow',
      sports: 'futebol',
      newsletter: '',
      contract: true,
      colors: [],
      todos: [
        {
          "userId": 1,
          "id": 1,
          "title": "delectus aut autem",
          "completed": false,
          "imgSrc": 'https://via.placeholder.com/150',
        },
        {
          "userId": 1,
          "id": 2,
          "title": "quis ut nam facilis et officia qui",
          "completed": false,
          "imgSrc": 'https://via.placeholder.com/150',
        },
        {
          "userId": 1,
          "id": 3,
          "title": "fugiat veniam minus",
          "completed": false
        },
        {
          "userId": 1,
          "id": 4,
          "title": "et porro tempora",
          "completed": true
        },
        {
          "userId": 1,
          "id": 5,
          "title": "laboriosam mollitia et enim quasi adipisci quia provident illum",
          "completed": false
        },
      ]
    }
  },
  methods: {
    onClick($evt) {
      // $evt = evento
      console.log('click', $evt);
    },
    onMouseOver() {
      console.log('onMouseOver');
    },
    onSubmit($evt) {
      console.log('submit', $evt);
    },
    onKeyUp($evt) {
      console.log('onKeyUp', $evt);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.title {
  font-size: 20px;
  color: blue;
}

.title-home {
  font-size: 40px;
  color: green;
}
</style>
