<script setup lang="ts">
import { reactive, ref, type DefineComponent, computed } from "vue";

import UploadImage from "./UploadImage.vue";
import Information from "./Information.vue";

const emit = defineEmits(["update:modelValue"]);
const props = defineProps({
    modelValue: {
        type: Object,
        default: {
            imageUrl: "",
            information: {
                fullname: "",
                currentpos: "",
                phone: "",
                mail: "",
                linkedin: "",
                github: "",
                profskill: "",
                techskill: ""
            }
        }
    }
});
const sideData = computed(() => props.modelValue);

function onChange(event: Event) {
    emit("update:modelValue", sideData);
    console.log("emitted update:modelValue in Side")
}
</script>

<template>
    <main>
        <UploadImage @change="onChange" v-model="sideData.imageUrl" />
        <Information @change="onChange" v-model="sideData.information" />
    </main>
</template>

<style scoped>
main {
    background-color: rgb(12, 85, 61);
}
</style>