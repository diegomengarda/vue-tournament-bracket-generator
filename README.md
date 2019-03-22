# Vue Tournament Bracket Generator
Generate tournament brackets easily

![Example](https://github.com/diegomengarda/vue-tournament-bracket-generator/tree/master/docs/images/example.gif)

## Quick Start

Install using npm:

```bash
npm install diegomengarda/vue-tournament-bracket-generator --save
```

Then import in your project:

```js
import VueTournamentBracketGenerator from 'vue-tournament-bracket-generator';

export default {
  components: {
    VueTournamentBracketGenerator
  }
}
```
```html
<template>
    <vue-tournament-bracket-generator :bracket-size="16"/>
</template>
```
