<template>
  <div>
    <div class="cell" @click="onClickSelf()">
      <template v-if="a"> {{text}}</template>
      <template v-else></template>
    </div>
  </div>

</template>

<script>
export default {
  props: ['n', 'finish'],
  data() {
    return {
      a: false,
      text: ''
    }
  },
  methods: {
    onClickSelf() {
      if (this.text || this.finish) return
      this.a = true
      this.text = this.n % 2 ? 'x' : 'o'
      this.$emit('click', this.text)
    }
  }
}
</script>

<style>
.cell {
  border: 1px solid red;
  width: 100px;
  height: 100px;
  font-size: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>