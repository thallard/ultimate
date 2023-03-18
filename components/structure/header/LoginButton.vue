<template>
    <div id="login-container">
        <Button id="connection-button" text="Connect wallet" v-on:click.native="connectWallet" v-if="connected == false"/>
        <div v-else>
            <div id="profile-container" >
                <img src="../../../static/image.jpeg"/>
                <a>{{ this.account }}</a>
            </div>
            <div id="dropdown-container">
                <ul id="dropdown-options">
                    <li>Settings</li>
                    <li v-on:click="disconnectWallet"><a>Disconnect</a></li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import Button from '../../UI/Button.vue'
import { defineComponent } from '@vue/composition-api'

export default defineComponent({
  components: { Button },
  data: function () {
    return {
        account: "",
        connected: false,
    }
  },
  methods: {
    connectWallet: async function () {
        // Connect to Metamask
        (window as any).ethereum.request({method: 'eth_requestAccounts' }).catch((e: Error) => {
            console.error(e.message);
            return ;
        }).then((result: string) => {
            const size = result[0].length;

            this.account = result[0].substring(0, 6) + "..." + result[0].substring(size - 4, size);
            this.connected = true;
           
        });
        // Remove login button and set profile image
        (document as any).getElementById("connection-button").style.display = "none";
    },
    disconnectWallet: async function () {
        // Handle Metamask
        if ((window as any).ethereum.isConnected()) {
            this.account = "";
            this.connected = false;
        }
    },
  }, 
});
</script>


<style>
img {
    border-radius: 50%;
    min-width: 16px;
    max-width: 32px;
}

#profile-container {
    display: flex;
    flex-direction: row;
    border-radius: 25px;
    border: 1.5px solid #5c5c5c;
    padding: 3px;
}

#profile-container:hover {
    border: 1.5px solid white;
    transition: all .25s;
}

#profile-container:active {
    background-color: #2C2C2C;
}

#profile-container a {
    margin: 0.5vh 0.5vw 0 0.5vw;
}

#dropdown-container {
    background-color: #1c1c1c;
    position: absolute;
    top: 3.5rem;
    right: 3rem;
    font-size: 0.9rem;
    padding: 10px;
    border-radius: 15%;
    border: 1.5px solid #5c5c5c;
}

#dropdown-container li:hover {
    cursor: pointer;
    background-color: #2C2C2C;
}
</style>