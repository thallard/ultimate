<template>
    <nav id="navbar">
        <div id="content-container">
            <div id="test">Organizations</div>
            
            <LoginButton class="right"/>
        </div>
    </nav>
</template>

<script lang="ts">
import Button from '../../UI/Button.vue'
import LoginButton from './LoginButton.vue'

export default {
  components: { Button, LoginButton },
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
#navbar {
    height: 6vh;
    border-bottom: 2px solid #2C2C2C;
}

#content-container {
    margin-top: 1vh;
    display: flex;
    flex-direction: row;
}

#content-container div {
    margin-left: 1%;
    margin-top: 1.5vh;
    margin-right: 1%;
}

.right {
    margin-left: 83.5%;
}


</style>