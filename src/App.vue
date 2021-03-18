<template>
  <div>
    n的值：{{n}}
    <div class="row">
      <Cell @click="onClickCell()" :n="n"/>
      <Cell @click="onClickCell()" :n="n"/>
      <Cell @click="onClickCell()" :n="n"/>
    </div>

    <div class="row">
      <Cell @click="onClickCell()" :n="n"/>
      <Cell @click="onClickCell()" :n="n"/>
      <Cell @click="onClickCell()" :n="n"/>
    </div>

    <div class="row">
      <Cell @click="onClickCell()" :n="n"/>
      <Cell @click="onClickCell()" :n="n"/>
      <Cell @click="onClickCell()" :n="n"/>
    </div>
  </div>
</template>

<script>
import Cell from '@/components/Cell'

export default {
  components: {
    Cell
  },

  data(){
    return {
      n: 0
    }
  },

  methods: {
    onClickCell() {
      console.log('某个Cell被点击了')
      this.n += 1
    }
  }

}
</script>

<style>
.row {
  display: flex;
}
</style>
