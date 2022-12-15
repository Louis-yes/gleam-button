<script setup lang="ts">
import GleamButton from "./components/GleamButton.vue";
</script>

<template>
  <main>
    <div class="wrapper">
      <h1>Louis' code test for Gleam</h1>
      <article>
        <p>Here's the default, primary button</p>
        <section>
          <GleamButton />
          <GleamButton :icon="true" />
          <GleamButton :icon-only="true"></GleamButton>
          <GleamButton :disabled="true" />
        </section>
        <section>
          <GleamButton :badge-count="3" />
          <GleamButton :badge-count="3" :icon="true" />
          <GleamButton :badge-count="3" :icon-only="true" />
          <GleamButton :badge-count="3" :disabled="true" />
        </section>
      </article>
      <article>
        <p>Here's the button in ghost mode</p>
        <section>
          <GleamButton class="ghost" />
          <GleamButton class="ghost" :icon="true" />
          <GleamButton class="ghost" :icon-only="true"></GleamButton>
          <GleamButton class="ghost" :disabled="true" />
        </section>
        <section>
          <GleamButton class="ghost" :badge-count="3" />
          <GleamButton class="ghost" :badge-count="3" :icon="true" />
          <GleamButton class="ghost" :badge-count="3" :icon-only="true" />
          <GleamButton class="ghost" :badge-count="3" :disabled="true" />
        </section>
      </article>
    </div>
  </main>
</template>

<style scoped></style>
