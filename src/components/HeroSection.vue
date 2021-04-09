
<template>
  <section class="hero">
    <article>
      <h1>Alpire</h1>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Est sunt officiis eveniet quasi ea quae ab culpa laboriosam quia exercitationem, mollitia doloribus! Fuga architecto atque aliquam libero obcaecati veritatis numquam?
      </p>
    </article>
    <div class="cubes">
      <rotating-cube>
        <template v-slot:a-side>
          <div class="cube-image cube-image-1"></div>
        </template>
        <template v-slot:b-side>
          <h3>
            The first image
          </h3>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Officia, expedita?</p>
        </template>
      </rotating-cube>
      <rotating-cube>
        <template v-slot:a-side>
          <div class="cube-image cube-image-2"></div>
        </template>
        <template v-slot:b-side>
          <h3>
            The second image
          </h3>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Officia, expedita?</p>
        </template>
      </rotating-cube>
      <rotating-cube>
        <template v-slot:a-side>
          <div class="cube-image cube-image-3"></div>
        </template>
        <template v-slot:b-side>
          <h3>
            The third image
          </h3>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Officia, expedita?</p>
        </template>
      </rotating-cube>
      <rotating-cube>
        <template v-slot:a-side>
          <div class="cube-image cube-image-4"></div>
        </template>
        <template v-slot:b-side>
          <h3>
            The fourth image
          </h3>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Officia, expedita?</p>
        </template>
      </rotating-cube>
    </div>
    <div class="centered">
      <a href="#contactus" class="prompt">Contact Now</a>
    </div>
  </section>
</template>

<script setup>
  import RotatingCube from './RotatingCube.vue'
</script>
<style>
section.hero {
  background: linear-gradient(to bottom, var(--primary-A200), var(--primary-A200) var(--header-height), var(--secondary-A200));
  width: 100vw;
  min-height: 100vh;
  position: relative;
  padding-top: 20vh;
  padding-left: 30px;
  padding-right: 30px;
}
section.hero article {
  margin: 0 auto;
  max-width: 640px;
  padding: 20px 0;
}
section.hero article h1 {
  text-align: center;
  color: var(--primary-500-contrast);
}
section.hero article p {
  color: var(--primary-500-contrast);
}

.prompt {
  text-decoration: none;
  padding: 12px 48px;
  font-size: 1.3rem;
  border-radius: 4px;
  border: 2px solid var(--accent-700);
  color: var(--accent-700);
  background-color: hsla(var(--accent-100-h), var(--accent-100-s), var(--accent-100-l), 30%) ;
  font-weight: bold;
  cursor: pointer;
  transition: 0.2s;
}
.prompt:hover {
  background-color: hsla(var(--accent-100-h), var(--accent-100-s), var(--accent-100-l), 40%) ;
}
.centered {
  text-align: center;
}
.cubes {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 2rem auto;
}
.cubes .cube {
  margin: 1rem;
}

.cubes .cube .b-side {
  padding: 1rem;
}
.cubes .cube .b-side h3, .cubes .cube .b-side p{
  margin: 0;
}
.cubes .cube .cube-image {
  height: 100%;
  width: 100%;
  background-image: url("../assets/splashscreen.jpg");
  background-size: cover;
  background-position: center;
}
.cubes .cube .cube-image-1 {
  background-image: url("../assets/monitor-1307227_1920.jpg");
}
.cubes .cube .cube-image-2 {
  background-image: url("../assets/startup-849804_1920.jpg");
}
.cubes .cube .cube-image-3 {
  background-image: url("../assets/computer-768608_1920.jpg");
}
.cubes .cube .cube-image-4 {
  background-image: url("../assets/computer-1185626_1920.jpg");
}

</style>