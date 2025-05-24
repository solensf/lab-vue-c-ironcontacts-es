<script setup>
import contactsDB from './contacts.json';
import { ref } from 'vue';
import Cards from './components/Cards.vue';

const contacts = ref(contactsDB.slice(0, 5));

function addRandomContact() {
  const remainingContacts = contactsDB.filter(
    (contact) => !contacts.value.includes(contact)
  );
  if (remainingContacts.length > 0) {
    const randomIndex = Math.floor(Math.random() * remainingContacts.length);
    const randomContact = remainingContacts[randomIndex];
    contacts.value.push(randomContact);
  } else {
    alert('No more contacts available to add!');
  }
}

function sortByName() {
  contacts.value.sort((a, b) => a.name.localeCompare(b.name));
}

function sortByPopularity() {
  contacts.value.sort((a, b) => b.popularity - a.popularity);
}

function deleteContact(contactId) {
  contacts.value = contacts.value.filter((contact) => contact.id !== contactId);
}
</script>

<template>
  <h1 class="tittle">IronContacts</h1>

  <div class="button-container">

    <button @click="addRandomContact">Add Random Contact</button>
    <button @click="sortByName">Sort by Name</button>
    <button @click="sortByPopularity">Sort by Popularity</button>
  </div>
  
  <table class="table">
    <thead>
      <th>Image</th>
      <th>Name</th>
      <th>Popularity</th>
      <th>Oscar</th>
      <th>Emmy</th>
      <th>Actions </th>
    </thead>
    <tbody>
      <Cards
        v-for="(contact, index) in contacts"
        :key="index"
        :tarjet="contact"
        @delete="deleteContact"
      />
    </tbody>
  </table>
</template>

<style>
.tittle {
  
  font-family: 'Cinzel', serif; 
  font-size: 3em; 
  color: #ffc107;
  text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.7); 
  text-align: center; 
  margin: 20px 0; 
  letter-spacing: 0.1em; 
}

/* Google Fonts import */
@import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@700&display=swap');

.button-container {
  display: flex;
  justify-content: center; 
  gap: 10px;
  margin-bottom: 20px;
}

.table {
  width: 90%; 
  margin: 0 auto; 
  border-collapse: collapse; 
  box-shadow: 0 0 10px rgba(221, 227, 36, 0.1); 
}

.table th, .table td {
  border: 1px solid #e41515; 
  padding: 12px; 
  text-align: center;
}

.table th {
  background-color: #8f2121; 
  font-weight: bold;
  color: #fafafa;
  text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.7); 

}

.table td {
  vertical-align: middle; 
}


</style>
