<script setup>
const props = defineProps({
  popularity: String,

});
 
</script>


<template>
<img :src="props.popularity"
   
    />
</template>

<style></style>