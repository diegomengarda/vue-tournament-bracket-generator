<script>
  const defaultRounds = [256, 128, 64, 32, 16, 8, 4, 2, 1]

  export default {
    name: 'vue-tournament-bracket-generator',
    props: {
      bracketSize: {
        type: Number,
        default: 8
      },
      matchStyle: {
        type: Object,
        default: () => ({
          border: '2px solid green',
          width: '100%',
          height: '30px',
          position: 'relative'
        })
      }
    },
    computed: {
      rounds () {
        return defaultRounds.filter(rounds => rounds <= this.bracketSize)
      }
    }
  }
</script>

<template>
    <div class="tournament-brackets">
        <div class="bracket">
            <template v-for="(round, index) in rounds">
                <div class="round" :key="index" :class="['round-' + round]">
                    <template v-for="(match, matchIndex) in round">
                        <div class="match" :key="matchIndex"><div class="match__content" :style="matchStyle"></div></div>
                    </template>
                </div>
            </template>
        </div>
    </div>
</template>

<style>
    *,
    *::after,
    *::before {
        box-sizing: border-box;
    }

    .bracket {
        display: flex;
    }

    .round {
        display: flex;
        flex-grow: 1;
        flex-direction: column;
    }

    .round:first-child .match::before {
        display: none;
    }

    .round:first-child .match__content::before {
        display: none;
    }

    .round:last-child .match::after {
        display: none;
    }

    .match {
        display: flex;
        flex-direction: column;
        justify-content: center;
        margin: 0 10px;
        padding: 6px 0;
        flex-grow: 1;
        position: relative;
    }

    .match::before {
        content: "";
        display: block;
        min-height: 30px;
        border-left: 2px solid purple;
        position: absolute;
        left: -10px;
        top: 50%;
        margin-top: -15px;
        margin-left: -2px;
    }

    .match:nth-child(odd)::after {
        content: "";
        display: block;
        border: 2px solid transparent;
        border-top-color: purple;
        border-right-color: purple;
        height: 50%;
        position: absolute;
        right: -10px;
        width: 10px;
        top: 50%;
    }

    .match:nth-child(even)::after {
        content: "";
        display: block;
        border: 2px solid transparent;
        border-bottom-color: purple;
        border-right-color: purple;
        height: 50%;
        position: absolute;
        right: -10px;
        width: 10px;
        bottom: 50%;
    }

    .match__content::before {
        content: "";
        display: block;
        width: 10px;
        border-bottom: 2px solid purple;
        margin-left: -2px;
        position: absolute;
        top: 50%;
        left: -10px;
    }
</style>
