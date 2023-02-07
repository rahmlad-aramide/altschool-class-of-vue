<template>
  <div>
    <h1>Color Picker Game</h1>
    <div>
      <div>{{ res }}</div>
    </div>
    <div class="buttons">
      <button v-for="color in colors" :key="color" @click="match(color)">
        {{ color }}
      </button>
    </div>
</div>
</template>

<script>
import { matchColor } from "../composables/use-color-match";
import { ref } from "vue";
export default {
  setup() {
    const colors = ["green", "red", "blue", "purple"];
    let res = ref("Pick a color...");
    const match = (color) => {
      let { message, messageColor } = matchColor(color, colors);
      console.log(messageColor)
      res.value = message;
    };
    return { res, match, colors };
  },
};
</script>


<style scoped>
  .body {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 80px;
  }
  .green {
    background-color: green;
  }
  .buttons {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
  }
</style>
