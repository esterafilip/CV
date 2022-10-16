<script setup lang="ts">
import InputComponent from "./InputComponent.vue";
import { ref } from "vue";

const fullname = ref("");
const currentpos = ref("");
const phone = ref("");
const mail = ref("");
const linkedin = ref("");
const github = ref("");
const profskill = ref("");
const techskill = ref("");
</script>

<template>
    <div class="wrapper-information">
        <p>Full Name*:</p>
        <input type="text" />
        <p>Current position:</p>
        <input type="text" />
        <h3>CONTACTS</h3>
        <p>Phone*:</p>
        <input type="number" />
        <p>Mail*:</p>
        <input type="email" />
        <p>LinkedIn:</p>
        <input type="url" />
        <p>Git:</p>
        <input type="url" />
        <h3>SKILLS</h3>
        <p>Professional:</p>
        <textarea></textarea>
        <p>Technical*:</p>
        <textarea></textarea>
    </div>
</template>

<style scoped lang="scss">
.wrapper-information {
    padding: 30px;
}

p {
    text-align: center;
}

input {
    width: 13rem;
    margin-bottom: 1rem;
    left: 1.5cm;
}

h3 {
    text-align: center;
    margin-top: 2rem;
    margin-bottom: 1rem;
}

textarea {
    width: 13rem;
    margin-bottom: 1rem;
    left: 1.5cm;
}
</style>