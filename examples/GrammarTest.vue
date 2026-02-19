<script setup lang="ts">
import { ref } from 'vue'

const items = ref([
  { id: 1, name: 'Sushi', active: true },
  { id: 2, name: 'Ramen', active: false },
  { id: 3, name: 'Udon', active: true }
])

const input = ref('')
const visible = ref(true)

function toggleVisibility() {
  visible.value = !visible.value
}

function addItem() {
  if (!input.value) return
  items.value.push({
    id: Date.now(),
    name: input.value,
    active: true
  })
  input.value = ''
}
</script>

<template>
  <main class="px-4 py-2 md:hover:bg-red-500">

    <!-- PascalCase component -->
    <MyButton @click="toggleVisibility" />

    <!-- v-model -->
    <input
      v-model="input"
      placeholder="Add item"
      class="px-4 py-2"
    />

    <!-- @click -->
    <button
      @click="addItem"
      :class="input ? 'bg-green-500 text-white' : 'bg-gray-300'"
    >
      Add
    </button>

    <!-- v-if -->
    <section v-if="visible">

      <!-- v-for -->
      <ul>
        <li
          v-for="item in items"
          :key="item.id"
          :class="item.active ? 'text-green-600' : 'text-gray-400'"
        >
          {{ item.name }}
        </li>
      </ul>

      <!-- Slots test -->
      <MyCard>

        <!-- v-slot:default -->
        <template v-slot:default>
          <p>Default slot via v-slot</p>
        </template>

      </MyCard>

      <!-- Slot shorthand -->
      <MyCard>
        <template #default>
          <p>Default slot via shorthand</p>
        </template>
      </MyCard>

    </section>

  </main>
</template>

<style scoped>
main {
  border: 1px solid #ccc;
  padding: 16px;
}
</style>
