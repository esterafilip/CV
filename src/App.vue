<script setup lang="ts">
import Side from "./components/Side.vue"
import Content from "./components/Content.vue";
import ButtonComponent from "./components/ButtonComponent.vue";

import { reactive } from "vue";

const initialState = {
  side: {
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
  },
  content: {
    about: "",
    work: "",
    education: "",
    languages: "",
    licence: ""
  }
}

const stateData = reactive({ ...initialState });

function reset() {
  Object.assign(stateData, initialState);
}

// *********************************************************************
//
//       function validate() {
//         return resumeData.name != "" && resumeData.education != "";
//       }
//
// *********************************************************************


function validate() {
  return true
}

function submit() {
  if (validate()) {
    alert("Sucessfully submitted")
    reset()
  } else {
    alert("Not all mandatory fields are filled!")
  }
}

</script>

<template>
  <header>
    <div class="grid-container">
      <Side v-model="stateData.side" />
      <Content v-model="stateData.content" />
      <div class="button-wrapper">
        <ButtonComponent msg="Submit" @click="submit" />
        <ButtonComponent msg="Reset" @click="reset" />
      </div>
    </div>
  </header>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.button-wrapper {
  display: flex;
  grid-area: 'content';
  flex-direction: row;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
  }

  header .wrapper {
    width: 100%;
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;
    padding: 1rem 0;
    margin-top: 1rem;
  }
}

.grid-container {
  width: 100%;
  display: grid;
  grid-template-columns: 1fr 3fr;
  grid-template-rows: 1fr max-content;
}

.grid-container>div {
  text-align: center;
  font-size: 30px;
  margin: 10px;
}
</style>
