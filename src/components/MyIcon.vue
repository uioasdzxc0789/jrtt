<template>
  <i class="toutiao toutiao-yanzhengma" :class="'toutiao-' + name"></i>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      require: true
    }
  },
  created () { },
  data () {
    return {}
  },
  methods: {},
  computed: {},
  watch: {},
  filters: {},
  components: {}
}
</script>

<style scoped>
</style>
