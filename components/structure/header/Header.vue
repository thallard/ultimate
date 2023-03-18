<template>
    <nav id="navbar">
        <a id="burger-button">
            <span class="bar"></span>
            <span class="bar"></span>
        </a>
        <div>
            <ul id="navbar-links">
                <li>Organizations</li>
            </ul>
        </div>
        <LoginButton id="login-button"/>      
    </nav>
</template>

<script lang="ts">
import Button from '../../UI/Button.vue'
import LoginButton from './LoginButton.vue'

export default {
    components: { Button, LoginButton },
    mounted() {
        (document as any).getElementById('login-button').style.paddingRight = "0.5%";
    },
}
</script>

<style>
#navbar {
    height: 6vh;
    background-color: #0c0c0c;
    /* border-bottom: 2px solid #2C2C2C; */
    font-size: 1rem !important;
    justify-content: space-between;
    align-items: center;
    display: flex;
}

#navbar-links {
    display: flex;
}

#navbar-links li {
    margin: 0 10px 0 10px;
}

#login-button {
    padding-right: 0.5%;
}

#burger-button  {
    position: absolute;
    top: 1.25rem;
    left: 1rem;
    display: none;
    flex-direction: column;
    justify-content: space-between;
    width: 30px;
    height: 16px;
}

#burger-button .bar {
    height: 3px;
    width: 100%;
    background-color: white;
    border-radius: 10px;
}

@media (max-width: 500px) {
    #burger-button {
        display: flex;
    }

    #navbar-links {
        display: none;
    }


}



</style>