<template>
  <div>
    {{n}}
    <div class="cell" @click="onClickSelf()">
      <template v-if="a">{{text}}</template>
      <template v-else>空</template>
    </div>
  </div>

</template>

<script>
export default {
  props:['n'],
  data: function data() {
    return {
      a: false,
      text: ''
    }
  },

  methods:{
    onClickSelf(){
      if(this.text !== '') return
      this.a = true
      this.text = this.n % 2 === 0 ? 'x' : 'o'
      this.$emit('click')
    }
  }
}
</script>

<style scoped>
.cell{
  border: 1px solid red;
  width: 100px;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 60px;

}
</style>