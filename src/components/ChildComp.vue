<script>
export default {
  emits: ['response'],
  created() {this.$emit('response', 'hello from child')
  },
  props: {
    msg: String
  }
}
</script>

<template>
  <slot>Fallback content</slot>
</template>