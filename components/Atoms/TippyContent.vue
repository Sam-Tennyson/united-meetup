<script setup lang="ts">

const route = useRoute();
const userStore = useUserStore()
const { logout } = userStore
const { isAuthenticated } = storeToRefs(userStore)

</script>
<template>
  <div class="bg-white border border-gray-400 shadow-lg p-4 rounded-lg text-sm min-w-60 ">
    <div class="flex flex-col gap-4">
      <NuxtLink :to="ROUTE_CONSTANTS.EVENTS">
        {{ STRING_DATA.YOUR_EVENTS }}
      </NuxtLink>
      <NuxtLink :to="ROUTE_CONSTANTS.GROUPS">
        {{ STRING_DATA.YOUR_GROUPS }}
      </NuxtLink>
      <hr class="bg-gray-500" />
      <template v-if="isAuthenticated">
        <NuxtLink class="cursor-pointer" @click="logout">
          {{ STRING_DATA.LOGOUT }}
        </NuxtLink>
      </template>
    </div>
  </div>
</template>
