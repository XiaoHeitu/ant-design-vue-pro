<template>
  <div>
    <render-dom parentTag="a-space" :vNode="this.btns">
      <a-dropdown v-if="menus.length > 0">
        <a-button :size="size">
          其他
          <a-icon type="down" />
        </a-button>
        <render-dom parentTag="a-menu" :vNode="this.menus" slot="overlay"></render-dom>
      </a-dropdown>
    </render-dom>
  </div>
</template>
<script>
import EButton from './EButton.vue'
import RenderDom from './RenderDom.vue'
export default {
  name: 'EButtonGroup',
  components: { EButton, RenderDom },
  props: {
    maxCount: {
      type: Number,
      default: 2
    },
    size: { type: String, default: 'default' }
  },
  data () {
    return {
      btns: [],
      menus: []
    }
  },
  created () {
    var count = this.$slots.default.length
    var bcount = count
    if (count > this.maxCount) {
      bcount = this.maxCount - 1
    }
    for (var i = 0; i < count; i++) {
      this.$slots.default[i].componentOptions.propsData.size = this.size
      if (i < bcount) {
        this.$slots.default[i].componentOptions.propsData.kind = 'button'
        this.btns.push(this.$slots.default[i])
      } else {
        this.$slots.default[i].componentOptions.propsData.kind = 'menuitem'
        this.menus.push(this.$slots.default[i])
      }
    }
  },
  methods: {}
}
</script>
