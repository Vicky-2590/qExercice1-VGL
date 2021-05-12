<template>
  <div class="card shadow-1">
    <img :src= plat.image width="198" height="180">
    <div class="card-content">
      <h1 class="text-primary">{{ plat.nom }}</h1>
      <p>{{ plat.description }}</p>
      <p>
        <small>
          <b>Note:</b>
        </small>
        <b class="text-primary">
          {{ plat.note }} / 5
        </b>
      </p>
      <q-btn @click="$emit('supprimer', plat.id)"
             class="full-width q-ma-md"
             color="secondary"
             icon="delete"
             label="Supprimer">
      </q-btn>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    plat: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>

</style>
