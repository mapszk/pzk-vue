<template>
  <!-- BUTTON -->
  <button
    class="button"
    :class="getStyles"
    :style="getMargin"
    v-if="!link"
  >
    <slot></slot>
  </button>
  <!-- LINK -->
  <router-link
    :to="href"
    v-if="link && !external"
    custom
    v-slot="{navigate, href}"
  >
    <button
      @click="navigate"
      class="button"
      :class="getStyles"
      :style="getMargin"
    >
      <slot></slot>
    </button>
  </router-link>
  <!-- EXTERNAL LINK -->
  <a
    v-if="link && external"
    :href="href"
    target="_blank"
    rel="noreferrer noopener"
    :class="getStyles"
    class="button"
  >
    <slot></slot>
  </a>
</template>

<script>
export default {
  name: 'Button',
  props: {
    link: { type: Boolean },
    href: { type: String },
    external: { type: Boolean },
    color: { type: String, required: true },
    variant: { type: String },
    full: { type: Boolean },
    mt: { type: String },
    mb: { type: String },
    mr: { type: String },
    ml: { type: String }
  },
  computed: {
    getStyles () {
      return {
        primary: this.color === 'primary',
        secondary: this.color === 'secondary',
        ghostPrimary: this.variant === 'ghost' && this.color === 'primary',
        ghostSecondary: this.variant === 'ghost' && this.color === 'secondary',
        full: this.full === true
      }
    },
    getMargin () {
      return {
        '--mt': this.mt,
        '--mb': this.mb,
        '--mr': this.mr,
        '--ml': this.ml
      }
    }
  }
}
</script>

<style scoped>
a{
  margin: 0;
  padding: 0;
  text-decoration: none;
  display: inline-block;
}
.button{
  margin-top: var(--mt);
  margin-bottom: var(--mb);
  margin-right: var(--mr);
  margin-left: var(--ml);

  cursor: pointer;
  font-weight: 600;
  display: flex;
  justify-content: center;
  align-items: center;
  outline: none;
  height: 2.5rem;
  width: max-content;
  min-width: 150px;
  /* padding: 0 2rem; */
  border-radius: 2.5rem;
  transition: transform .5s ease;
}
.button:hover{
  transform: translateY(-3px);
}

.full{
  width: 100%;
}
.primary{
  background-color: #052b36;
  color: white;
  border: 2px solid #052b36;
}
.secondary{
  background-color: #c8ff30;
  color: #052b36;
  border: 2px solid #c8ff30;
}
.ghostPrimary{
  border: 2px solid #052b36;
  background-color: transparent;
  color: #052b36;
}
.ghostSecondary{
  border: 2px solid #c8ff30;
  background-color: transparent;
  color: #c8ff30;
}
</style>
