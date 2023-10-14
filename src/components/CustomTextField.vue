<template>
  <v-text-field clearable
    v-bind="$attrs"
    v-model="data"
    >
  </v-text-field>
</template>

<script setup lang="ts">
  import {ref, computed } from "vue";
  import {} from "vue"

  const props = defineProps<{modelValue:string}>();
  const emits = defineEmits<{
    (e:"update:modelValue", text:string): void;
  }>();

const data = computed({
    get(){
        return props.modelValue;
    },
    set(value:string){
        console.log(value)
        emits("update:modelValue", convert(value))
    }
})

// Delete more than 10 characters in a text field.
const convert = (target:string) =>{
    if(target.length > 10){
        return target.substring(0,10)
    }
    return target;
}
</script>
