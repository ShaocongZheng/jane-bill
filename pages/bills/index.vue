<template>
  <!-- <div> -->
  <v-card class="mx-auto">
    <v-dialog v-model="formDialog" persistent hide-overlay max-width="400">
      <v-card class="mx-auto">
        <v-card-title>
          <span class="headline">账单</span>
        </v-card-title>
        <v-container>
          <v-form ref="form" lazy-validation class="white" max-width="300px">
            <v-text-field
              v-model="billForm.bill"
              label="金额"
              required
              outlined
            ></v-text-field>
            <v-text-field
              v-model="billForm.desc"
              label="备注"
              required
              clearable
              outlined
            ></v-text-field>
          </v-form>
        </v-container>
      </v-card>
    </v-dialog>
    <v-card dark flat>
      <v-btn
        absolute
        bottom
        color="teal lighten-2"
        right
        fab
        @click="handleNewBill"
      >
        <v-icon>mdi-plus</v-icon>
      </v-btn>
      <v-card-title class="pa-2 teal darken-1">
        <v-btn icon>
          <v-icon>mdi-menu</v-icon>
        </v-btn>
        <h3 class="title font-weight-light text-center grow">Timeline</h3>
        <v-avatar>
          <v-img
            src="https://avataaars.io/?avatarStyle=Circle&topType=LongHairStraight&accessoriesType=Blank&hairColor=BrownDark&facialHairType=Blank&clotheType=BlazerShirt&eyeType=Default&eyebrowType=Default&mouthType=Default&skinColor=Light"
          ></v-img>
        </v-avatar>
      </v-card-title>
      <v-img
        src="https://cdn.vuetifyjs.com/images/cards/forest.jpg"
        gradient="to top, rgba(0,0,0,.44), rgba(0,0,0,.44)"
      >
        <v-container class="fill-height">
          <v-row align="center">
            <strong class="display-4 font-weight-regular mr-6">8</strong>
            <v-row justify="end">
              <div class="headline font-weight-light">Monday</div>
              <div class="text-uppercase font-weight-light">February 2015</div>
            </v-row>
          </v-row>
        </v-container>
      </v-img>
    </v-card>
    <v-card-text class="py-0">
      <v-timeline dense clipped>
        <v-timeline-item
          v-for="(item, index) in dayBills"
          class="mb-4"
          :key="item.desc + index"
          :color="colors[index]"
          small
        >
          <v-row justify="space-between">
            <v-col cols="4" align-self="center">
              <strong>{{ item.time }}</strong>
            </v-col>
            <v-col cols="4">
              <strong>{{ item.consumption }}</strong>
              <div class="caption">{{ item.desc }}</div>
            </v-col>
          </v-row>
        </v-timeline-item>
        <v-timeline-item color="pink" small>
          <v-row class="pt-1">
            <v-col cols="3">
              <strong>5pm</strong>
            </v-col>
            <v-col>
              <strong>New Icon</strong>
              <div class="caption">Mobile App</div>
            </v-col>
          </v-row>
        </v-timeline-item>

        <v-timeline-item color="teal lighten-3" small>
          <v-row class="pt-1">
            <v-col cols="3">
              <strong>3-4pm</strong>
            </v-col>
            <v-col>
              <strong>Design Stand Up</strong>
              <div class="caption mb-2">Hangouts</div>
              <v-avatar>
                <v-img
                  src="https://avataaars.io/?avatarStyle=Circle&topType=LongHairFrida&accessoriesType=Kurt&hairColor=Red&facialHairType=BeardLight&facialHairColor=BrownDark&clotheType=GraphicShirt&clotheColor=Gray01&graphicType=Skull&eyeType=Wink&eyebrowType=RaisedExcitedNatural&mouthType=Disbelief&skinColor=Brown"
                ></v-img>
              </v-avatar>
              <v-avatar>
                <v-img
                  src="https://avataaars.io/?avatarStyle=Circle&topType=ShortHairFrizzle&accessoriesType=Prescription02&hairColor=Black&facialHairType=MoustacheMagnum&facialHairColor=BrownDark&clotheType=BlazerSweater&clotheColor=Black&eyeType=Default&eyebrowType=FlatNatural&mouthType=Default&skinColor=Tanned"
                ></v-img>
              </v-avatar>
              <v-avatar>
                <v-img
                  src="https://avataaars.io/?avatarStyle=Circle&topType=LongHairMiaWallace&accessoriesType=Sunglasses&hairColor=BlondeGolden&facialHairType=Blank&clotheType=BlazerSweater&eyeType=Surprised&eyebrowType=RaisedExcited&mouthType=Smile&skinColor=Pale"
                ></v-img>
              </v-avatar>
            </v-col>
          </v-row>
        </v-timeline-item>

        <v-timeline-item color="pink" small>
          <v-row class="pt-1">
            <v-col cols="3">
              <strong>12pm</strong>
            </v-col>
            <v-col>
              <strong>Lunch break</strong>
            </v-col>
          </v-row>
        </v-timeline-item>

        <v-timeline-item color="teal lighten-3" small>
          <v-row class="pt-1">
            <v-col cols="3">
              <strong>9-11am</strong>
            </v-col>
            <v-col>
              <strong>Finish Home Screen</strong>
              <div class="caption">Web App</div>
            </v-col>
          </v-row>
        </v-timeline-item>
      </v-timeline>
    </v-card-text>
  </v-card>
  <!-- </div> -->
</template>
<script lang="ts">
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

  created() {
    this.hello()
  }

  async hello() {
    // const response = await fetch('/api/p/136975432')
    // const myBlob = await response.blob()
    // console.log(myBlob)
    // console.log(1)
    // const objectURL = URL.createObjectURL(myBlob)
    // const image = document.createElement('img')
    // image.src = objectURL
    // document.body.appendChild(image)
  }

  // 计算属性
  private get color1() {
    return this.colors[0]
  }

  handleNewBill() {
    console.log('show', this.color1)
    this.formDialog = true
    setTimeout(() => {
      this.formDialog = false
    }, 3000)
  }
}
// export default {
//   data: () => ({
//     selectedItem: 1,
//     items: [
//       { text: '本月账单', icon: 'mdi-clock' },
//       { text: '', icon: 'mdi-account' },
//       { text: 'Conversions', icon: 'mdi-flag' },
//     ],
//     colors: [
//       'red',
//       'pink',
//       // 'purple',
//       'indigo',
//       'blue',
//       'cyan',
//       'teal',
//       'green',
//       'lime',
//       'yellow',
//       'amber',
//       'orange',
//       'brown',
//       'grey',
//     ],
//     dayBills: [
//       {
//         time: '8:00:00',
//         desc: '早餐',
//         consumption: 5,
//         img: '',
//       },
//       {
//         time: '12:00:00',
//         desc: '午餐',
//         consumption: 25,
//         img: '',
//       },
//       {
//         time: '12:00:00',
//         desc: '淘宝裤子',
//         consumption: 25,
//         img: '',
//       },
//       {
//         time: '12:00:00',
//         desc: '午餐',
//         consumption: 25,
//         img: '',
//       },
//       {
//         time: '18:00:00',
//         desc: '晚餐',
//         consumption: 28,
//         img: '',
//       },
//     ],
//     formDialog: false,
//     billForm: {
//       bill: '',
//       desc: '',
//     },
//   }),
//   created() {
//     console.log('created')
//   },
//   methods: {
//     handleNewBill() {
//       console.log('show')
//       this.formDialog = true
//       setTimeout(() => {
//         this.formDialog = false
//       }, 3000)
//     },
//   },
// }
</script>
