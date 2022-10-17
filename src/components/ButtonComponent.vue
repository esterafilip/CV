<script setup lang="ts">
defineProps({
    msg: {
        type: String,
        default: ""
    }
})
</script>

<template>
    <div class="wrapper-buttons">
        <button class="button" type="submit">{{msg}}</button>
    </div>
</template>

<style>
.wrapper-buttons {
    display: flex;
    padding: 50px;
    align-items: baseline;
    gap: 10rem;
}

.button {
    background-color: rgb(12, 85, 61);
    width: 6rem;
    height: 4rem;
    border: none;
    color: white;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    margin: 4px 2px;
}

.button:hover {
    background-color: green;
}
</style>
