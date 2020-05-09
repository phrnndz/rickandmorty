<template>
  <div class="column is-one-third">
    <div class="card large round">
      <div class="card-image">
        <figure class="image">
          <img v-bind:src="character.image" alt="Image">
        </figure>
      </div>
      <div class="card-content">
        <div class="content">
          <h2 class="title">{{ character.name }}</h2>
          <button class="button is-fullwidth">Ver más</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["character"]
};
</script>

