<template>

  <div class="max-w-sm rounded overflow-hidden shadow-lg flex content-center flex flex-col">
    <div class="mr-24 mb-4">
      <img class="animate-spin w-20 grid grid-cols-1" src="./assets/logo.svg">
    </div>
    <p>Nouvelle lettre: <br>{{ message }} </p>
    <p>Lettres déjà jouées: <br>{{ letters }}</p>
    <div class="px-6 py-4">
      <div v-if="isGenerated">
        <p> {{ error }}</p>
      </div>
    </div>
    <div class="px-6 pt-4 pb-2">
      <button class="bg-gray-700 hover:bg-gray-600 text-white font-bold py-2 px-4 rounded" v-on:click="generateLetter()">Lettre</button>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      message: '',
      letters: [],
      error: 'Je cherche une nouvelle lettre qui ne soit pas encore sortie',
      isGenerated: false
    }
  },
  components: {
  },
  methods: {
      rndStr(len) {
        let text = ""
        let chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"

        for( let i=0; i < len; i++ ) {
          text += chars.charAt(Math.floor(Math.random() * chars.length))
        }
        return text
      },
    generateLetter() {
      let message = this.rndStr(1)
      if(this.letters.indexOf(message) == -1) {
        this.message = message
        this.letters += message + '  '
        this.isGenerated = false

      }
      else {
        this.isGenerated = true
        return this.error
      }
    }
    },
    mounted () {

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
.rotate {
  transition: transform 1s ease-in-out;
  height: 20vmin;
}
.rotate:hover {
  transform: rotateZ(360deg);
}
</style>
