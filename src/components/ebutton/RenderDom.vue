<script>
export default {
  name: 'RenderDom',
  props: {
    vNode: { type: Array, default: null },
    parentTag: { type: String, default: 'div' }
  },
  render (h) {
    return h(this.parentTag, this.vNode.concat(this.$slots.default))
  }
}
</script>
