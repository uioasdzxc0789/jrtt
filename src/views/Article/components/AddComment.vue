<template>
  <van-field
    v-model.trim="message"
    rows="2"
    autosize
    type="textarea"
    maxlength="50"
    placeholder="请输入留言"
    show-word-limit
    class="add-field"
    ref="field"
  >
    <template #extra
      ><van-button
        type="default"
        :disabled="message.length === 0"
        @click="onClick"
        >发布</van-button
      ></template
    >
  </van-field>
</template>

<script>
import { addComment } from '@/api/comment'
export default {
  props: {
    target: {
      type: [Number, String],
      required: true
    },
    art_id: {
      type: [Number, String]
    }
  },
  created () { },
  data () {
    return {
      message: ''
    }
  },
  methods: {
    async onClick () {
      try {
        const res = await addComment({
          target: this.target, content: this.message, art_id: this.art_id
        })
        console.log(res)
        this.$emit('add-comment', res.data.data.new_obj)
      } catch (err) {
        console.log(err)
      }
    }
  },
  computed: {},
  watch: {},
  filters: {},
  components: {},
  mounted () {
    // 组件最终会变成dom结构，$el可以获取这个组件的根标签
    this.$refs.field.$el.querySelector('textarea').focus()
  }
}
</script>

<style scoped lang='less'>
.add-field {
  align-items: center;
  button {
    border: none;
  }
}
</style>
