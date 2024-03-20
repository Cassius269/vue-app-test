<script setup lang="ts">
import { ref } from 'vue' // importation de la méthode ref() pour la création de variables

// Création d'un objet avec les informations d'un utilisateur
const fahami = ref({
  firstName: 'Fahami',
  lastName: 'Mohamed Ali',
  age: 31,
  origin: 'Comores'
})

// Transformation du firstname en array
const firstName = fahami.value.firstName.split('')

// Utilisation de l'affectation par décomposition pour séparer la lettre du reste du prénom
let [first, ...rest] = firstName

console.log(first)

console.log(firstName)

console.log(fahami.value)

// test du v-html
const name = '<i>Jean</i>'

console.log(name)
</script>
<template>
  <h1 v-if="fahami !== null">
    Bonjour
    <span>{{ `${first.toUpperCase()}${rest.join('')} ${fahami.lastName.toUpperCase()} ! ` }}</span>
  </h1>
  <p>
    Vous êtes originaire
    {{ fahami.origin[fahami.origin.length - 1] === 's' ? 'des' : 'de' }}
    {{ fahami.origin }}
  </p>

  <!---test v-html-->
</template>
<style scoped>
h1 {
  background-color: rgb(143, 98, 98);
}
</style>
