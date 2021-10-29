<template>
  <section id="hero">
      <div class="heroImages">
        <div class="monitor">
          <img src="/images/monitor.png" alt="monitor" />
        </div>
        <div class="baldeAzul">
          <img src="/images/balde-azul.png" alt="pintura" />
        </div>
        <div class="baldeVerde">
          <img src="/images/balde-verde.png" alt="pintura" />
        </div>
        <div class="cubo">
          <img src="/images/cubo.png" alt="cubo" />
        </div>
        <div class="esfera">
          <img src="/images/esfera.png" alt="esfera" />
        </div>
      </div>
      <div class="heroText">
        <h2>
          Hi! I'm Martín Pilaszek, <br />
          and I'm front-end developer.
        </h2>
        <div class="heroButtons">
          <Button color="primary" variant="ghost" link href="/projects">Projects</Button>
          <Button mt=".5rem" color="primary" link href="/contact">Contact</Button>
        </div>
      </div>
    </section>
</template>

<script>
import Button from '../components/Button.vue'

export default {
  name: 'Home',
  components: { Button }
}
</script>

<style scoped>
/* IMAGES */
.monitor {
  z-index: 1;
  grid-column: 2 / 4;
  grid-row: 2 / 4;
  width: 100%;
  animation: floatMonitor 8s ease-in-out infinite alternate;
}
.baldeAzul {
  width: 100%;
  height: 100%;
  grid-column: 1 / 3;
  grid-row: 1 / 3;
  display: flex;
  justify-content: flex-start;
  align-items: flex-end;
  animation: floatPintura 5s ease-in-out 1s infinite alternate;
}
.baldeAzul img {
  width: 50%;
  transform: translateX(35px);
}
.baldeVerde {
  z-index: 1;
  width: 100%;
  height: 100%;
  grid-column: 5 / 3;
  grid-row: 5 / 3;
  display: flex;
  justify-content: center;
  align-items: center;
  animation: floatPintura 6s ease-in-out 2s infinite alternate;
}
.baldeVerde img {
  width: 50%;
}
.cubo {
  grid-column: 1 / 3;
  grid-row: 3 / 5;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  padding-right: 5rem;
  animation: floatFigura 5s ease-in-out infinite alternate;
}
.cubo img {
  width: 50%;
}
.esfera {
  grid-column: 3 / 5;
  grid-row: 1 / 3;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  padding-left: 4rem;
  padding-top: 3rem;
  animation: floatFigura 5s ease-in-out infinite alternate;
}
.esfera img {
  width: 35%;
}
img {
  width: 100%;
}

.heroButtons {
  margin-top: 1rem;
  display: flex;
  width: 100%;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.heroButtons:last-child{
  margin-top: .5rem;
}

.heroImages {
  padding: 0 0 2rem 0;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(4, 1fr);
  justify-content: center;
  align-items: center;
  animation: 3s fallAnim;
}

.heroText {
  padding: 2rem 0;
  display: flex;
  text-align: center;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  animation: 2s fallAnim;
  color: #052b36;
}

@media screen and (min-width: 720px) {
  #hero{
    display: flex;
    height: 500px;
  }
  .heroButtons{
    align-items: flex-start;
  }
  .heroText{
    align-items: flex-start;
    text-align: left;
    flex: 4;
    order: -1;
    font-size: 30px;
    text-align: left;
  }
  .heroImages{
    padding: 2rem 0 2rem 0;
    flex: 5;
  }
}

/* ANIMATIONS */
@keyframes floatMonitor {
  0% {transform: translateY(0)}
  0% {transform: translateY(14px)}
}
@keyframes floatPintura {
  0% {transform: translateY(0)}
  100% {transform: translateY(17px)}
}
@keyframes floatFigura {
  0% {transform: translateY(0)}
  0% {transform: translateY(20px)}
}
@keyframes fallAnim {
  0% {transform: translateY(-3rem); opacity: 0;}
  100% {transform: translateY(0); opacity: 1;}
}

</style>
