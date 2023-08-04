<script setup lang="ts">
import axios from '@axios'

const response = await axios.get('http://localhost:3000/data')
</script>

<template>
  <div>
    <VCard
      class="mb-6"
      title="Kick start your project 🚀"
    >
      <VCardText>All the best for your new project.</VCardText>
      <VCardText>
        Please make sure to read our <a
          href="https://demos.pixinvent.com/vuexy-vuejs-admin-template/documentation/"
          target="_blank"
          rel="noopener noreferrer"
          class="text-decoration-none"
        >
          Template Documentation
        </a> to understand where to go from here and how to use our template.
      </VCardText>
    </VCard>

    <VCard title="VCard">
      <VCardText>
        <p>
          Name:  {{ response.data.name }}
        </p>
        <p>
          Technology: {{ response.data.technology }}
        </p>
      </VCardText>
    </VCard>
  </div>
</template>
