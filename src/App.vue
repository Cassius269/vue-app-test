<script setup lang="ts">
import { idText } from 'typescript';
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

// Utilisation de l'affectation par décomposition pour séparer la lettre du reste du prénom pour la présention
let [first, ...rest] = firstName

// test du v-html
const name = '<i>Jean</i>' //<i> est une balise HTML

// le binding de propriété: v-bind sert à associer des valeurs de propriétés dans les attributs HTML
const presentation = ref('presentation'); // utilisation de la liaison de propriété dans le pargraphe à la classe presentation
const paragrapheEnfance = ref("paragrapheEnfance");
const size = ref("40"); // propriété size utilisé dans le paragraphe de la passion pour la photographie

// utilisation des fonctions
const getType = ()=>{
  return 'date';
}

const getTitle = () => 'La scolarité'; // cette fonction retourne une valeur lorsqu'elle est déclarée sur une ligne et sans 



</script>
<template>
  <h1 v-if="fahami !== null">
    Bonjour
    <span>{{ `${first.toUpperCase()}${rest.join('')} ${fahami.lastName.toUpperCase()} ! ` }}</span>
  </h1>
  <p :class="presentation">
    Vous êtes originaire
    {{ fahami.origin[fahami.origin.length - 1] === 's' ? 'des' : 'de' }}
    {{ fahami.origin }}
  </p>

  <!---test v-html-->
  <p v-html="name"></p>

  <!---Utilisation de v-bind-->
  <p :class="paragrapheEnfance">Vous avez passé votre enfance à Moroni dans la béatitude et la serenité qui caracterise le climat</p>
  <p :style="{fontSize: `${size}px`,color:'red'}">Vous avez une passion pour la photographie</p>

  <input :type="getType()">

  <h3>{{ getTitle() }}</h3>
</template>
<style scoped>
h1 {
  background-color: rgb(143, 98, 98);
}

.presentation {
  color: goldenrod;
}

.paragrapheEnfance {
  background-color: gray;
  padding: 3px;
}
</style>
