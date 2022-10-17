<script setup lang="ts">
import WelcomeItem from "./WelcomeItem.vue";
import IconEducation from "./icons/IconEducation.vue";
import IconExperience from "./icons/IconExperience.vue";
import IconLanguage from "./icons/IconLanguage.vue";
import IconAboutMe from "./icons/IconAboutMe.vue";
import IconLicenceCert from "./icons/IconLicenceCert.vue";
import InputComponent from "./InputComponent.vue";
import { reactive, ref, computed } from "vue";

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
  console.log("emitted update:modelValue in TheWelcome")
}
</script>

<template>
  <WelcomeItem>
    <template #icon>
      <IconAboutMe />
    </template>

    <InputComponent @change="onChange" v-model="resumeData.about" label="About" :multiline="true" />
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <IconExperience />
    </template>

    <InputComponent @change="onChange" v-model="resumeData.work" label="Work" :multiline="true" :mandatory="true" />
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <IconEducation />
    </template>

    <InputComponent @change="onChange" v-model="resumeData.education" label="Education" :multiline="true"
      :mandatory="true" />
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <IconLanguage />
    </template>

    <InputComponent @change="onChange" v-model="resumeData.languages" label="Languages" :multiline="true" />
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <IconLicenceCert />
    </template>

    <InputComponent @change="onChange" v-model="resumeData.licence" label="Licenses" :multiline="true" />
  </WelcomeItem>
</template>
