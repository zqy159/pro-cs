<template>
  <div>
    {{a}}
  </div>
</template>

<script>
export default {
  props: {
    a: {
      type: Boolean,
      required: true
    }
  },
  watch: {
    a() {
      console.log(11111)
    }
  }
}
</script>


