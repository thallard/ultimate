<template>
    <Header />

</template>

<script>
import Header from '~/components/structure/header/Header.vue'
export default {
  components: { Header },
  mounted() {
    if (typeof window.ethereum !== 'undefined')
      console.log('MetaMask is installed!');
    else
      console.log('no Metamask');
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans:wght@600&display=swap');

html, body, #__nuxt, #__layout{
  height:100% !important;
  margin: 0 !important;
  background: #1C1C1C;
  color: white;
  font-family: 'Noto Sans', sans-serif;
}

</style>
