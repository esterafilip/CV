<script setup lang="ts">
import WelcomeItem from "./WelcomeItem.vue";
import IconEducation from "./icons/IconEducation.vue";
import IconExperience from "./icons/IconExperience.vue";
import IconLanguage from "./icons/IconLanguage.vue";
import IconAboutMe from "./icons/IconAboutMe.vue";
import IconLicenceCert from "./icons/IconLicenceCert.vue";
import InputComponent from "./InputComponent.vue";
import { ref } from "vue";

const initialState = {
  about: "",
  work: "",
  education: "",
  languages: "",
  licence: ""
};
</script>

<template>
  <WelcomeItem>
    <template #icon>
      <IconAboutMe />
    </template>
    <template #heading>About me</template>
    
    <InputComponent v-model="about" />
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <IconExperience />
    </template>
    <template #heading>Work experience*</template> 

    <InputComponent v-model="work" />
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <IconEducation />
    </template>
    <template #heading>Education*</template>
    
    <InputComponent v-model="education" />
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <IconLanguage />
    </template>
    <template #heading>Languages</template>
    
    <InputComponent v-model="languages" />
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <IconLicenceCert />
    </template>
    <template #heading>Licenses & certifications</template>
    
    <InputComponent v-model="licence" />
  </WelcomeItem>
</template>
