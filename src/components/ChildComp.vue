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
<div>child component</div>
  <p>{{msg}}</p>
</template>