<template>
  <section class="hero is-primary has-background">
    <img
      alt="Fill Murray"
      class="hero-background is-transparent"
      src="https://media.cnnchile.com/sites/2/2020/04/rick_y_morty_7132_1570805482-740x430.jpg"
    >
    <div class="hero-body">
      <div class="columns">
        <div class="column is-12">
          <div class="container content">
            <h1 class="title">THE RICK AND MORTY</h1>
            <h3 class="subtitle">I GOT ONE RIGHT HERE, GRAB MY TERRY FLAP</h3>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {};
</script>

<style>
.hero.has-background {
  position: relative;
  overflow: hidden;
}
.hero-background {
  position: absolute;
  object-fit: cover;
  object-position: center center;
  width: 100%;
  height: 100%;
}
.hero-background.is-transparent {
  opacity: 0.3;
}
</style>


