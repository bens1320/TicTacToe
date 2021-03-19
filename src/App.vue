<template>
  <div>
    n的值：{{n}}
    <div class="row">
      <Cell @click="onClickCell(0, $event)" :n="n" :finished="finished"/>
      <Cell @click="onClickCell(1, $event)" :n="n" :finished="finished"/>
      <Cell @click="onClickCell(2, $event)" :n="n" :finished="finished"/>
    </div>

    <div class="row">
      <Cell @click="onClickCell(3, $event)" :n="n" :finished="finished"/>
      <Cell @click="onClickCell(4, $event)" :n="n" :finished="finished"/>
      <Cell @click="onClickCell(5, $event)" :n="n" :finished="finished"/>
    </div>

    <div class="row">
      <Cell @click="onClickCell(6, $event)" :n="n" :finished="finished"/>
      <Cell @click="onClickCell(7, $event)" :n="n" :finished="finished"/>
      <Cell @click="onClickCell(8, $event)" :n="n" :finished="finished"/>
    </div>
    {{map}}
    {{result}}
    {{finished}}
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
      finished: false
    }
  },

  methods: {
    onClickCell(i, text) {
      console.log(`${i} 号被点击了为：${text}`)
      this.map[Math.floor(i / 3)][i % 3] = text
      this.n += 1
      this.tell(text)
    },

    tell(text){
      const map = this.map
      for(let i=0; i<3; i++){
        if(map[i][0] && map[i][0] === map[i][1] && map[i][1] === map[i][2]){
          this.result =  map[i][2]
        }
      }

      for(let i=0; i<3; i++){
        if(map[0][i] && map[0][i] === map[1][i] && map[1][i] === map[2][i]){
          this.result =  map[2][i]
        }
      }

      if(map[0][0] && map[0][0] === map[1][1] && map[1][1] === map[2][2]){
        this.result = map[2][2]
      }

      if(map[0][2] && map[0][2] === map[1][1] && map[1][1] === map[2][0]){
        this.result = map[2][0]
      }
      if(this.result){
        this.finished = true
      }
    }

  }

}
</script>

<style>
.row {
  display: flex;
}
</style>
