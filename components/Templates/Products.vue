<script setup lang="ts">

const addProductRequest = async () => {
  const payload = {
    title: 'test product',
    price: 13.5,
    description: 'lorem ipsum set',
    image: 'https://i.pravatar.cc',
    category: 'electronic'

  }
  const response = await postRequest(ENDPOINTS.TODOS, payload)
  await getRequest(ENDPOINTS.TODOS)
}

const addProduct = () => {
  addProductRequest()
}

const todoStore = useTodosStore()
const { data: storeTodoData } = storeToRefs(todoStore)

</script>
<template>
  <div class="flex items-center justify-start gap-4">
    <button class="btn btn-secondary btn-sm" @click="addProduct()">Add product</button>
  </div>
  <h2 v-for="(todo, index) in storeTodoData">
    <span class="font-bold">
      <NuxtLink :to="ROUTE_CONSTANTS.PRODUCTS + '/' + todo.id">
        {{ todo.id }}
      </NuxtLink>
    </span>
    {{ todo.title }}
  </h2>
</template>
