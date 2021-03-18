<template>
  <div class="cell" @click="a = true">
    <template v-if="a">x</template>
    <template v-else>空</template>
  </div>
</template>

<script>
export default {
  data: function data() {
    return {
      a: false
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