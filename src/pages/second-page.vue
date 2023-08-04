<script setup lang="ts">
import axios from '@axios'

type Data = {
  name: string
  technology: string
} | null

const data = ref<Data>()
const showLoader = ref(true)
const isLoading = ref(true)

axios.get('http://localhost:3000/data').then(response => {
  data.value = response.data
  console.log(data.value)
  showLoader.value = false
  if (isLoading.value === true)
    isLoading.value = false
})

const test = (stopLoading: () => void) => {
  setTimeout(stopLoading, 3000)
}
</script>

<template>
  <div>
    <AppCardActions
      class="mb-6"
      title="App Card Action"
      action-refresh
      @refresh="test"
    >
      <VCardText>
        <p>Name: {{ data?.name }}</p>
        <p>Technology: {{ data?.technology }}</p>
      </VCardText>
    </AppCardActions>

    <VCard
      :loading="showLoader"
      title="VCard"
      class="mb-6"
    >
      <VCardText>
        <p>Name: {{ data?.name }}</p>
        <p>Technology: {{ data?.technology }}</p>
      </VCardText>
    </VCard>

    <AppCardActions
      v-model:loading="isLoading"
      class="mb-6"
      title="App Card Action"
      @refresh="test"
    >
      <VCardText>
        <p>Name: {{ data?.name }}</p>
        <p>Technology: {{ data?.technology }}</p>
      </VCardText>
    </AppCardActions>
  </div>
</template>
