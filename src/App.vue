<template>
  <div id="app" class="principal-container">
    <v-header></v-header>
    <v-emoji></v-emoji>
    <v-piano></v-piano>
  </div>
</template>

<script>
import VHeader from '@/components/VHeader'
import VEmoji from '@/components/VEmoji'
import VPiano from  '@/components/VPiano'
export default {
  name: "App",
  components: {
    VHeader,
    VEmoji,
    VPiano,
  },
};
</script>

<style lang="postcss"  scoped>
.principal-container{
    background: linear-gradient(rgba(255, 157, 108, 1), rgba(187, 78, 117, 1));
    background-size: 100%;
    height: 100vh; 
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
}
</style>