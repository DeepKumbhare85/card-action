<script setup lang="ts">
import axios from '@axios'

const data = await axios.get('http://localhost:3000/data')
</script>

<template>
  <VCard>
    <VCardText>
      {{ data.data.name }}
    </VCardText>
  </VCard>
</template>
