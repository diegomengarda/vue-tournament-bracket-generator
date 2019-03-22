<script>
  const defaultRounds = [128, 64, 32, 16, 8, 4, 2, 1]

  export default {
    name: 'vue-tournament-bracket-generator',
    props: {
      bracketSize: {
        type: Number,
        default: 16
      }
    },
    computed: {
      rounds () {
        return defaultRounds.filter(rounds => rounds < this.bracketSize)
      }
    }
  }
</script>

<template>
    <div class="tournament-brackets">
        <div class="bracket">
            <template v-for="round in rounds">
                <div class="round" :class="['round-' + (round * 2)]">
                    <template v-for="match in round">
                        <div class="match">
                            <div class="match__content"></div>
                        </div>
                        <div class="match">
                            <div class="match__content"></div>
                        </div>
                    </template>
                </div>
            </template>
            <div class="round round-1">
                <div class="match"><div class="match__content"></div></div>
            </div>
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
        margin: 0px 10px;
        padding: 30px 0;
        flex-grow: 1;
        position: relative;
    }

    .match::before {
        content: "";
        display: block;
        height: 30px;
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

    .match__content {
        border: 2px solid green;
        width: 100%;
        height: 20px;
        position: relative;
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
