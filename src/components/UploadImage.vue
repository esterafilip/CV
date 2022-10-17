<template>
    <div class="wrapper-upload">
        <h3>Choose a profile image</h3>
        <img alt="" :src="imageUrl" width="150" height="150" />
        <input id="hiddenInput" type="file" @change="onFileSelected" style="display: none" />
        <button @click="onBrowse">Browse...</button>
    </div>
</template>
  
<script setup lang="ts">
import { computed, ref } from "vue";

const emit = defineEmits(["update:modelValue"]);
const props = defineProps({
    modelValue: {
        type: String,
        default: "",
    },
});

const imageUrl = computed(() => props.modelValue);

function onBrowse() {
    document.getElementById("hiddenInput")?.click();
}

function onFileSelected(event: Event) {
    const target = event.target as HTMLInputElement;
    const files = target.files;

    if (!files || !files[0]) return;

    emit("update:modelValue", URL.createObjectURL(files[0]));
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

button {
    width: 6rem;
}

img {
    border-radius: 50%;
    border: 7px solid rgb(111, 120, 43);
}
</style>