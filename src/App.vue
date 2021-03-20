<template>
  <div class="wrapper">
    第 {{n}} 手：
    <div class="chess">
      <div class="row">
        <Cell @click="onClickCell(0, $event)" :n="n" :finish="finish"/>
        <Cell @click="onClickCell(1, $event)" :n="n" :finish="finish"/>
        <Cell @click="onClickCell(2, $event)" :n="n" :finish="finish"/>
      </div>

      <div class="row">
        <Cell @click="onClickCell(3, $event)" :n="n" :finish="finish"/>
        <Cell @click="onClickCell(4, $event)" :n="n" :finish="finish"/>
        <Cell @click="onClickCell(5, $event)" :n="n" :finish="finish"/>
      </div>


      <div class="row">
        <Cell @click="onClickCell(6, $event)" :n="n" :finish="finish"/>
        <Cell @click="onClickCell(7, $event)" :n="n" :finish="finish"/>
        <Cell @click="onClickCell(8, $event)" :n="n" :finish="finish"/>
      </div>
    </div>
    结果：{{ !result ? '胜负未分' : `${result} 获胜！！！`}}
  </div>
</template>

<script>
import Cell from '@/components/Cell'


export default {
  components: {
    Cell
  },
  data() {
    return {
      n: 0,
      map: [
        [null, null, null],
        [null, null, null],
        [null, null, null],
      ],
      result: '',
      finish: false
    }
  },
  methods: {
    onClickCell(i, text) {
      this.map[Math.floor(i / 3)][i % 3] = text
      this.n += 1
      this.tell()
    },

    tell() {
      const map = this.map
      if (map[0][0] && map[0][0] === map[1][1] && map[1][1] === map[2][2]) {
        this.result = map[0][0]
      }
      if (map[0][2] && map[0][2] === map[1][1] && map[1][1] === map[2][0]) {
        this.result = map[0][2]
      }
      for (let i = 0; i < 3; i++) {
        if (map[i][0] && map[i][0] === map[i][1] && map[i][1] === map[i][2]) {
          this.result = map[i][0]
        }
      }
      for (let i = 0; i < 3; i++) {
        if (map[0][i] && map[0][i] === map[1][i] && map[1][i] === map[2][i]) {
          this.result = map[0][i]
        }
      }
      if (this.result) this.finish = true
    }
  }
}
</script>

<style>
.wrapper{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.row {
  display: flex;
}
</style>
