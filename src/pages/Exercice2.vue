<template>
  <!--
    Exercice 2 - Listes et composants Vue.js

OK    1) Créez un tableau pour les plats,  que vous voyez sur la page.
       Chaque objet du tableau doit contenir les propriété suivantes
       image (url de l’image), nom, description et note (note de 1 à 5)

 OK   2) Créer une boucle v-for qui affiche ces aliments sur la page,
       avec toutes les données provenant du tableau des aliments
       (indice : pour l’image, à la place de l'attribut src,
       utiliser la directive :src)

OK   3) Ajoutez un de vos plats préférés à la liste
       Vous pouvez trouver des images ici : https://imgur.com/

OK    4) Créez un composant enfant pour les plats(components/Plat.vue)
       et utilisez-le pour afficher chacun de vos plats

OK    5) Dans le tableau des plats, ajoutez un identifiant unique (id)
       à chaque plats.
       Appliquez l'id à une propriété :key de votre boucle v-for.

    6) Ajouter un lien ou un bouton supprimer à votre composant enfant Plat,
       qui émettra un événement "supprimer" et passera l'id du plat.

    7) Dans la page, écouter l'événement "supprimer" et supprimer le plat
       du tableau des plats.

  -->
  <q-page padding>
    <div class="q-pa-md row items-stretch">
      <plat v-for="plat in plats" :key="plat.id" :plat="plat" v-on:supprimer="deletePlat">
      </plat>
    </div>
  </q-page>
</template>

<script>
import Plat from 'components/Plat'

export default {
  components: { Plat },
  data () {
    return {
      plats: [
        {
          id: '1',
          image: 'https://i.imgur.com/0umadnY.jpg',
          nom: 'Burger',
          description: 'Un hamburger est un sandwich composé d\'une ou plusieurs\n' +
            '            tranches de viande hachée, généralement du bœuf, placées\n' +
            '            dans un petit pain ou une brioche.',
          note: '4'
        },
        {
          id: '2',
          image: 'https://i.imgur.com/b9zDbyb.jpg',
          nom: 'Pizza',
          description: 'La pizza est un plat savoureux d\'origine italienne, consistant\n' +
            '            en une base généralement ronde et aplatie de\n' +
            '            pâte levée à base de blé.',
          note: '5'
        },
        {
          id: '3',
          image: 'https://i.imgur.com/RbKjUjB.jpg',
          nom: 'Petits choux',
          description: 'Le chou de Bruxelles est une variété de chou, plante herbacée\n' +
            '            de la famille des Brassicaceae. C’est vraiement pas bon...',
          note: '1'
        },
        {
          id: '4',
          image: 'https://i.imgur.com/BrfUA3D.jpeg',
          nom: 'Taco',
          description: 'Un taco est un antojito de la cuisine mexicaine qui se compose d\'une tortilla de maïs repliée\n ' +
            'ou enroulée sur elle-même contenant presque toujours une garniture le plus souvent à base de viande,\n ' +
            'de sauce, d\'oignon et de coriandre fraiche hachée. Les tacos se mangent généralement sans couverts,\n ' +
            'avec les doigts.',
          note: '3'
        }

      ]
    }
  },
  methods: {
    deletePlat (id) {
      this.plats = this.plats.filter(function (plat) {
        return plat.id !== id
      })
    }
  }
}
</script>

<style>
.card {
  flex-basis: 210px;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 5px;
  margin-right: 10px;
  margin-bottom: 10px;
}

.card img {
  max-width: 100%;
}

.card-content {
  padding: 0 10px;
}

h1 {
  font-size: 23px;
}

p {
  font-size: 14px;
}
</style>
