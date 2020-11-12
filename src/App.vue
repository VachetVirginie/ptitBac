<template>
  <img class="rotate" src="./assets/logo.svg">
  <button v-on:click="generateLetter()">Lettre</button>
  <p>{{ message }} </p>
  <p>{{ letters }}</p>
  <div v-if="isGenerated">
    <p> {{ error }}</p>
  </div>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      message: '',
      letters: [],
      error: 'Je cherche une nouvelle lettre qui ne sois pas encore sortie',
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
