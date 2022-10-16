<template>
    <div class="wrapper-upload">
        <h3>Choose a profile image</h3>
        <img alt="" :src="imageSrc" width="150" height="150" />
        <input id="hiddenInput" type="file" placeholder="Browse" @change="onFileSelected" style="display: none" />
        <button @click="onBrowse">Browse...</button>
    </div>
</template>
  
<script setup lang="ts">
import { ref } from "vue";

const imageSrc = ref();

function onBrowse() {
    document.getElementById("hiddenInput")?.click();
}

function onFileSelected(event: Event) {
    const target = event.target as HTMLInputElement;
    const files = target.files;

    if (!files || !files[0]) return;

    imageSrc.value = URL.createObjectURL(files[0]);
    console.log(imageSrc);
}
</script>
  
<style scoped lang="scss">
.wrapper-upload {
    display: flex;
    flex-direction: column;
    padding: 30px;
    gap: 20px;
    align-items: center;
}
button{
    width: 6rem;
}
img {
    border-radius: 50%;
    border: 7px solid rgb(111, 120, 43);
}
</style>