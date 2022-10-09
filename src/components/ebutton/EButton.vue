<template>
  <div>
    <a-button size="small" type="danger" v-if="type!='menu'">
      <slot></slot>
    </a-button>
    <!-- <a-menu-item size="small" type="danger" v-if="type='menu'">
      <slot name="this.menuslot"></slot>
    </a-menu-item> -->
  </div>
</template>

<script>
export default {
  name: 'EButton',
  components: {},
  props: {
    type: { type: String, default: 'button' }
  },
  data () {
    return {
      btnslot: '',
      menuslot: ''
    }
  },
  created () {
    if (this.type === 'menu') {
      this.menuslot = 'default'
    } else {
      this.btnslot = 'default'
    }
  },
  mounted () {
    console.log(this)
  },
  methods: {}
}
</script>
