<template>
  <v-card class="mx-auto">
    <v-img
      class="white--text align-end"
      src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
    >
      <v-card-title>Top 10 Australian beaches</v-card-title>
    </v-img>

    <v-card-subtitle class="pb-0"> Number 10 </v-card-subtitle>

    <v-card-text class="text--primary">
      <div>hope you can win a prize in a lottery</div>

      <div>lottery: {{ lottery }}</div>
      <div>specialNum: {{ specialNum }}</div>
    </v-card-text>

    <v-card-actions>
      <v-btn color="orange" text> Today's lottery </v-btn>

      <v-btn color="orange" text @click="reRandom"> Random </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script lang="ts">
import _ from 'lodash'
import { Component, Vue } from 'vue-property-decorator'
@Component
export default class bills extends Vue {
  colors = [
    'red',
    'pink',
    // 'purple',
    'indigo',
    'blue',
    'cyan',
    'teal',
    'green',
    'lime',
    'yellow',
    'amber',
    'orange',
    'brown',
    'grey',
  ]

  dayBills = [
    {
      time: '8:00:00',
      desc: '早餐',
      consumption: 5,
      img: '',
    },
    {
      time: '12:00:00',
      desc: '午餐',
      consumption: 25,
      img: '',
    },
    {
      time: '12:00:00',
      desc: '淘宝裤子',
      consumption: 25,
      img: '',
    },
    {
      time: '12:00:00',
      desc: '午餐',
      consumption: 25,
      img: '',
    },
    {
      time: '18:00:00',
      desc: '晚餐',
      consumption: 28,
      img: '',
    },
  ]

  formDialog = false
  billForm = {
    bill: '',
    desc: '',
  }

  lottery = this.generateLotter()
    .slice(0, 5)
    .sort((a: number, b: number) => a - b)

  specialNum = this.generateLotter(1, 12)
    .slice(0, 2)
    .sort((a: number, b: number) => a - b)

  generateLotter(min: number = 1, max: number = 35): Array<number> {
    let arrs: number[] = []
    for (let i = min; i <= max; i++) {
      arrs.push(i)
    }
    arrs = _.shuffle(arrs)
    return arrs
  }

  reRandom(): void {
    this.lottery = this.generateLotter()
      .slice(0, 5)
      .sort((a: number, b: number) => a - b)
    this.specialNum = this.generateLotter(1, 12)
      .slice(0, 2)
      .sort((a: number, b: number) => a - b)
  }
}
</script>
