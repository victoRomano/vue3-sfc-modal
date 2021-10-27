<template>
  <h1>{{ title }}</h1>
  <p>{{ description }}</p>
  <teleport to="#modals" v-if="showModalA">
    <Modal theme="sale" @close="toggleModalA">
      <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>Sign up for Giveaway!</h1>
      <p>some modal content</p>
      <button @click="toggleModalB">Open Modal B</button>
    </Modal>
  </teleport>

  <teleport to="#modals" v-if="showModalB">
    <Modal @close="toggleModalB">
      <h1>Sign up to newslatter</h1>
      <p>For updates and promo codes!</p>
    </Modal>
  </teleport>

  <button @click="toggleModalA">Open Modal A</button>
  <button @click="toggleModalB">Open Modal B</button>
</template>

<script setup>
import { ref } from "@vue/reactivity";
import Modal from "./components/Modal.vue";

const title = ref("Vue 3 (SFC) Modal");
const description = ref(
  "Modal project - custom modal component using new teleport feature"
);
const showModalA = ref(false);
const showModalB = ref(false);

const toggleModalA = () => {
  showModalA.value = !showModalA.value;
};
const toggleModalB = () => {
  showModalB.value = !showModalB.value;
};
</script>

<style>
#app,
#modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
