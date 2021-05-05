<template>
  <!--
  Exercice 1

 OK 1) Créer les données (data) name et age

 OK 2) Reliez ces données aux deux champs de saisie <input /> correspondants

 OK 3) Afficher le nom et l'âge dans le cadre beige <div class="description"> (première ligne en gras)

 OK 4) Utilisez une propriété calculée pour afficher l'âge plus 10 ans (deuxième ligne en gras)

 Ok 5) Afficher le nombre de caractères du nom (troisième ligne en gras)
OK 6) Utilisez un filtre pour afficher le nom en majuscules (quatrième ligne en gras)

 OK 7) N'affichez le cadre beige que si un nom et un âge valide ont été saisis.
     Sinon, affichez le cadre rouge <div class="no-details">

 OK 8) Utilisez v-show pour afficher les messages d'erreur à côté des champs
     si le nom comporte plus de 15 caractères et l'âge dépasse 100 ans
     ou est plus petit que 1.

  9) Ajouter la classe CSS "error" aux champs de saisie s'ils enfreignent les mêmes règles

  10) Lorsque vous cliquez sur le bouton "Générer une personne",
      vous générez un nom aléatoire (à partir d'un tableau que vous créerez) et
      un âge aléatoire compris entre 1 et 100 ans.
      Ces nouvelles valeurs doivent être mise à jour partout dans la vue.

  11) Créer une directive qui donnera le focus au champ nom lors du chargement de la page

  12) Faites en sorte qu'une personne aléatoire soit générée lors du premier chargement de la page
  -->
  <q-page padding>
    <div className="form q-mb-lg">
      <div className="row q-mb-md">
        <label>Nom:</label>
        <input v-model="nom">
        <label v-show="nbLettreNom > 15" className="error">Maximum 15 caractères
        </label>
      </div>
      <div className="row q-mb-md">
        <label>Age:</label>
        <input v-model="age">
        <label v-show="age < 1 || age >= 100" className="error">Veuillez entrer un âge compris entre 1 et 100</label>
      </div>
      <div className="row">
        <button>Générer une personne</button>
      </div>
    </div>
    <!--Cadre beige -->
    <div v-if="age >= 1 && age < 100 && nbLettreNom < 15" className="description q-mb-lg">
      <p>Mon nom est <b>{{ nom }}</b> et j'ai <b>{{ age }}</b> ans.</p>
      <p>Dans 10 ans, j'aurai <b>{{ agePlus10 }}</b> ans.</p>
      <p>Mon nom se compose de <b>{{ nbLettreNom }}</b> caractères.</p>
      <p>Mon nom en majuscules est <b>{{ nomEnMaj }}</b>.</p>
    </div>
    <!--Cadre rouge -->
    <div v-else className="no-details">
      <p>Veuillez entrer un nom et un âge valide !</p>
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'PageExercice1',
  data () {
    return {
      nom: '',
      age: ''
    }
  },
  computed: {
    agePlus10 () {
      if (isNaN(this.age) || this.age === '') {
        return 0
      }
      // chaque texte provenant d'Internet doit être reconverti en nombre pour être calculé
      return parseInt(this.age) + 10
    },
    nbLettreNom () {
      return this.nom.length
    },
    nomEnMaj () {
      return this.nom.toUpperCase()
    }
  }
}
</script>

<style>
.form {
  background: #eee;
  padding: 10px;
}

label {
  min-width: 70px;
}

label.error {
  font-size: 13px;
  color: red;
  margin-left: 5px;
  margin-top: 3px;
}

input {
  border: 1px solid #ccc;
}

input.error {
  border: 1px solid red;
  background: pink;
}

.description {
  background: antiquewhite;
  padding: 20px 20px 7px;
}

.no-details {
  background: lightcoral;
  padding: 20px 20px 7px;
}
</style>
