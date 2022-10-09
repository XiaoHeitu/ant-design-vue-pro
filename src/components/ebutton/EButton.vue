<template>
  <component :is="component" :class="cssclass" :size="size" :type="type" @click="onclick">
    <slot></slot>
  </component>
</template>
<script>
export default {
  name: 'EButton',
  components: {},
  props: {
    size: { type: String, default: 'default' },
    type: { type: String, default: 'default' },
    kind: { type: String, default: 'button' }
  },
  data () {
    return { component: 'a-menu-item', cssclass: 'ant-dropdown-menu-item' }
  },
  created () {
    if (this.kind === 'button') {
      this.component = 'a-button'
      this.cssclass = ''
    } else if (this.kind === 'menuitem') {
      this.component = 'a-menu-item'
      this.cssclass = 'ant-dropdown-menu-item'
    }
  },
  mounted () {},
  methods: {
    onclick () {
      this.$emit('click')
    }
  }
}
</script>
