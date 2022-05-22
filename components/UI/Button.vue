<template>
    <button>{{ text }}</button>
</template>

<script lang="ts">

export default {
props: ['text']
}
</script>

<style>
button {
    margin: 0 !important;
    border: 1.5px solid #5C5C5C;
    text-align: center;
    background-color: transparent;
    width: auto;
    padding-right: 20px;
    padding-left: 20px;
    border-radius: 25px;
    height: 4.5vh;
    color: white;
    font-weight: 600;
    font-size: 100%;
    font-family: inherit;
}

button:hover {
    border: 1.5px solid white;
    transition: all .25s;
}

button:active {
    background-color: #2C2C2C;
}

</style>
