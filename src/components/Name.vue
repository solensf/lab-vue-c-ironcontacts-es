<script setup>
const props = defineProps({
  name: String,

});
 
</script>


<template>
<name :src="props.name"
          />
</template>

<style></style>