<script setup lang="ts">
import type { Character } from "../types/interfaces.ts"
const props = defineProps<{ character: Character }>();

const emit = defineEmits(['select']);
const selectCharacter = () => {
  emit('select', props.character);
};
console.log (props)
</script>
<template>
  <div class="hexagon" @click="selectCharacter">
    <img 
    :src="`/public/img/characters/${props.character.name.toLowerCase()}.png`" 
    :alt="props.character.name"
    class="w-24 h-24 mx-auto" />
    <h3 class="text-lg font-bold">{{ props.character.name }}</h3>
    <p>{{ props.character.class }}</p>
    <p v-if="props.character.playable"><span class="text-sm text-green-500">Playable Character</span></p>
  </div>
</template>

<style scoped>
.hexagon {
  width: 100px;
  height: 55px;
  background-color: #4A90E2;
  position: relative;
}

.hexagon:before,
.hexagon:after {
  content: "";
  position: absolute;
  width: 0;
  border-left: 50px solid transparent;
  border-right: 50px solid transparent;
}

.hexagon:before {
  bottom: 100%;
  border-bottom: 27.5px solid #4A90E2;
}

.hexagon:after {
  top: 100%;
  border-top: 27.5px solid #4A90E2;
}
</style>