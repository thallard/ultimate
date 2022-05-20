<template>
    <div id="login-container">
         <Button id="connection-button" v-on:click.native="connectWallet"/>
         <h6 id="login">{{ account == undefined ? "" : account[0] }}</h6>
    </div>
</template>

<script lang="ts">
import Button from '../../UI/Button.vue'

export default {
  components: { Button },
  data: function () {
      return {
          account: null,
      }
  },
  methods: {
    connectWallet: async function () {
        // Connect to Metamask
        this.account = await (window as any).ethereum.request({method: 'eth_requestAccounts' }).catch((e: Error) => {
            console.error(e.message);
            return ;
        });

        // Remove login button and set profile image
        (document as any).getElementById("connection-button").style.display = "none";
        (document as any).getElementById("login").style.display = "block";

    }
  },
}
</script>

<style>

</style>