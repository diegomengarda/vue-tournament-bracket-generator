# Vue Tournament Bracket Generator

Generate tournament brackets easily

Demo: **[Click Here](https://vue-tournament-bracket-generator.netlify.com)**

![Example](https://s2.gifyu.com/images/example88d0f690296efddd.gif)

## Quick Start

Install using npm:

```bash
npm install diegomengarda/vue-tournament-bracket-generator --save
```

Then import in your project:

```js
import VueTournamentBracketGenerator from "vue-tournament-bracket-generator";

export default {
  components: {
    VueTournamentBracketGenerator
  }
};
```

```html
<template>
  <vue-tournament-bracket-generator :bracket-size="16" />
</template>
```
