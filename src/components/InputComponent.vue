<template>
    <div class="input-wrap">
        <label>{{labelText}}</label>
        <textarea
        v-if="isMultiLine"
        :value="modelValue"
        @input="$emit('update:modelValue', ($event.target as HTMLTextAreaElement).value)"
        />
        <input 
        v-else-if="isNumber"
        :value="modelValue"
        type="number"
        @input="$emit('update:modelValue', ($event.target as HTMLInputElement).value)"
        />
        <input 
        v-else-if="isUrl"
        :value="modelValue"
        type="url"
        @input="$emit('update:modelValue', ($event.target as HTMLInputElement).value)"
        />
        <input 
        v-else-if="isEmail"
        :value="modelValue"
        type="email"
        @input="$emit('update:modelValue', ($event.target as HTMLInputElement).value)"
        />
        <input 
        v-else
        :value="modelValue"
        type="text"
        @input="$emit('update:modelValue', ($event.target as HTMLInputElement).value)"
        />
    </div>
</template>

<script setup lang="ts">
import {onMounted, ref} from "vue";

const props = defineProps({
    label: {
        type: String,
        default: "",
    },
    mandatory: {
        type: Boolean,
        default: false,
    },
    multiline: {
        type: Boolean,
        default: false,
    },
    number: {
        type: Boolean,
        default: false,
    },
    email: {
        type: Boolean,
        default: false,
    },
    url: {
        type: Boolean,
        default: false,
    },
    modelValue: {
        type: String,
        default: ""
    },
});

const isMandatory = ref(props.mandatory);
const isMultiLine = ref(props.multiline);
const labelText = ref(props.label);
const isNumber = ref(props.number);
const isEmail = ref(props.email);
const isUrl = ref(props.url);

onMounted(() => {
    if(isMandatory.value){
        labelText.value += "*"
    }
});
</script>

<style lang="scss" scoped>
.input-wrap{
    display: flex;
    flex-direction: column;
    width: 35rem;

    textarea{
        padding: 8px 12px;
        font-size: 18px;
    }
}
</style>