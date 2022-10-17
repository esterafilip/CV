<script setup lang="ts">
import HelloWorld from "./HelloWorld.vue";
import TheWelcome from "./TheWelcome.vue";
import ButtonComponent from "./ButtonComponent.vue";

import { reactive, computed } from "vue";

const emit = defineEmits(["update:modelValue"]);
const props = defineProps({
    modelValue: {
        type: Object,
        default: {
            about: "",
            work: "",
            education: "",
            languages: "",
            licence: ""
        }
    }
});

const resumeData = computed(() => props.modelValue);

function onChange(event: Event) {
    emit("update:modelValue", resumeData);
    console.log("emitted update:modelValue in Content")
}
</script>

<template>
    <main>
        <HelloWorld msg="Create your own CV!" />
        <br><br>
        <TheWelcome @change="onChange" v-model="resumeData" />
    </main>
</template>

<style scoped>

</style>
