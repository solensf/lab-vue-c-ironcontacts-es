<script setup>
import Name from './Name.vue';
import Picture from './Picture.vue';
import Popularity from './Popularity.vue';

const props = defineProps({
  tarjet: Object,
});

const emit = defineEmits(["delete"])

</script>

<template>
  <tr class="table">
    <td> <img class="image"
       :src='props.tarjet.pictureUrl'/></td>
    <td> {{ props.tarjet.name }}</td>
    <td> {{ props.tarjet.popularity.toFixed(2) }}</td>
    <td> {{ props.tarjet.wonOscar ? "🏆" : " "}}</td>
    <td> {{ props.tarjet.wonEmmy ? "🏆" : " " }}</td>
    <td> <button @click="()=> emit('delete', props.tarjet.id)"> delete </button></td>
  </tr>
</template>

<style scoped>
.image{
  height: 100px;
  border-radius: 50%;
}

.table{
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}
</style>
