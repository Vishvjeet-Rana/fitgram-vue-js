<script setup>
const { handleCloseModal } = defineProps({
  handleCloseModal: Function,
});
</script>

<template>
  <Teleport to="#portal">
    <section>
      <div class="portal-container">
        <div
          role="button"
          @click="handleCloseModal"
          tabindex="0"
          class="portal-underlay"
        ></div>
        <div class="portal-content">
          <slot />
        </div>
      </div>
    </section>
  </Teleport>
</template>

<style scoped>
.portal-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  z-index: 1001;
}

.portal-underlay {
  position: absolute;
  inset: 0;
  background-color: var(--background-primary);
  opacity: 0.7;
  z-index: 999;
  border: none;
  padding: none;
}

.portal-content {
  position: absolute;
  z-index: 1000;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 600px;
  max-width: 90vw;
  max-height: 80vh;
  display: grid;
  place-items: center;
  background: var(--background-primary);
  border-radius: var(--border-radius-small);
  border: 1px solid var(--background-muted);
  padding: 1rem;
}
</style>
