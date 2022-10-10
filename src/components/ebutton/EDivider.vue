<template>
  <component :is="component" :type="type" :orientation="orientation" :dashed="dashed" />
</template>
<script>
export default {
  name: 'EDivider',
  components: {},
  props: {
    dashed: { type: Boolean, default: false },
    orientation: { type: String, default: 'center' },
    type: { type: String, default: 'horizontal' },
    kind: { type: String, default: 'button' }
  },
  data () {
    return { component: 'a-divider' }
  },
  created () {
    if (this.kind === 'button') {
      this.component = 'a-divider'
    } else if (this.kind === 'menuitem') {
      this.component = 'a-menu-divider'
    }
  }
}
</script>
