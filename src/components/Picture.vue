<script setup>
const props = defineProps({
  picture: String,

});
 
</script>


<template>
<img :src="props.picture"
         />
</template>

<style></style>