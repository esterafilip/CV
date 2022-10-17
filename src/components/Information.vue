<script setup lang="ts">
import InputComponent from "./InputComponent.vue";
import { reactive, ref, computed } from "vue";

const emit = defineEmits(["update:modelValue"]);
const props = defineProps({
    modelValue: {
        type: Object,
        default: {
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
});

const resumeData = computed(() => props.modelValue);

function onChange(event: Event) {
    emit("update:modelValue", resumeData);
    console.log("emitted update:modelValue in Information")
}
</script>

<template>
    <div class="wrapper-information">
        <InputComponent @change="onChange" v-model="resumeData.fullname" label="Full Name" class="input"
            :mandatory="true" />
        <InputComponent @change="onChange" v-model="resumeData.currentpos" label="Current Position" class="input" />
        <h3>CONTACTS</h3>
        <InputComponent @change="onChange" v-model="resumeData.phone" label="Phone number" :number="true" class="input"
            :mandatory="true" />
        <InputComponent @change="onChange" v-model="resumeData.mail" label="Mail" :email="true" class="input"
            :mandatory="true" />
        <InputComponent @change="onChange" v-model="resumeData.linkedin" label="LinkedIn" :url="true" class="input" />
        <InputComponent @change="onChange" v-model="resumeData.github" label="Git" :url="true" class="input" />
        <h3>SKILLS</h3>
        <InputComponent @change="onChange" v-model="resumeData.profskill" label="Professional" :multiline="true"
            class="input" />
        <InputComponent @change="onChange" v-model="resumeData.techskill" label="Technical" :multiline="true"
            class="input" :mandatory="true" />
    </div>
</template>

<style scoped lang="scss">
.wrapper-information {
    padding: 30px;
}

.input {
    width: 13rem;
    margin-bottom: 1rem;
    left: 1.5cm;
}

h3 {
    text-align: center;
    margin-top: 2rem;
    margin-bottom: 1rem;
}
</style>