<template>
    <div id="app">
        <div class="config">
            <strong>Bracket Size:</strong>
            <input type="text"
                   v-model="size"
                   placeholder="256, 128, 64, 32, 16, 8, 4, 2">
        </div>
        <vue-tournament-bracket-generator :bracket-size="size"/>
    </div>
</template>

<script>
  import VueTournamentBracketGenerator from '../../src/components/VueTournamentBracketGenerator'

  export default {
    name: 'app',
    components: {
      VueTournamentBracketGenerator
    },
    data () {
      return {
        size: 8
      }
    }
  }
</script>

<style>
    #app {
        padding: 15px;
    }
    .config {
        padding-bottom: 15px;
        padding-left: 10px;
        font-size: 18px;
    }
    .config input {
        padding: 5px 12px;
        font-size: 16px;
    }
</style>
