<template>
  <div>
    <div class="row">
      <Cell/>
      <Cell/>
      <Cell/>
    </div>

    <div class="row">
      <Cell/>
      <Cell/>
      <Cell/>
    </div>

    <div class="row">
      <Cell/>
      <Cell/>
      <Cell/>
    </div>
  </div>
</template>

<script>
import Cell from '@/components/Cell'

export default {
  components: {
    Cell
  },

}
</script>

<style>
.row{
  display: flex;
}
</style>
