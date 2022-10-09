<template>
  <div>
    <slot></slot>
    <a-dropdown v-if="this.$children.length>maxCount">
      <a-button size="small">
        其他
        <a-icon type="down" />
      </a-button>
      <slot name="menus"></slot>
    </a-dropdown>
  </div>
</template>

<script>
export default {
  name: 'EButtonGroup',
  components: {},
  props: {
    maxCount: {
      type: Number,
      default: 2
    }
  },
  data () {
    return {}
  },
  created () {
    console.log(this)
    for (var i = 0; i < this.$children.length; i++) {
      var bcount = this.$children.length
      if (this.$children.length > this.maxCount) {
        bcount = this.maxCount - 1
      }
      if (i < bcount) {
        // this.$children[i].solt = 'btns'
      } else {
        this.$children[i].solt = 'menus'
        this.$children[i].type = 'menu'
      }
    }
  },
  mounted () {
    // console.log(this)
  },
  methods: {}
}
</script>
