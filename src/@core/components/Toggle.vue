<script setup lang="ts">
interface Emits {
  (e: 'toggleHidden', value: boolean): void
}

const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  hidden: {
    type: Boolean,
    default: undefined,
  },
})

const emits = defineEmits<Emits>()

const _hidden = ref(false)

const toggleHidden = () => {
  if (props.hidden !== undefined)
    emits('toggleHidden', props.hidden)
  else
    _hidden.value = !_hidden.value
}

const $hidden = computed(() => {
  return props.hidden !== undefined ? props.hidden : _hidden.value
})
</script>

<template>
  <div>
    <button @click="toggleHidden">
      Toggle
    </button>
    <h1>
      {{ title }}
    </h1>

    <slot v-if="$hidden" />
  </div>
</template>
