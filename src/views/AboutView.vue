vue <template lang="">
  <div>
    <h1>Counter -><span>{{counter}}</span></h1>
    <button @click='this.counter--'>Decrement</button>
    <button @click='this.counter++'>Increment</button>
    <h1 v-show="check">This contains the v-show</h1>
    <ul>
      <!--list rendering-->
      <!--<li v-for="sport,index in  sports" :key="index">{{sport}}</li>-->
      <li v-for="({message},index) in objects" :key="index">{{message}}</li>
    </ul>
    <!--one way data binding-->
    <h3>{{oneWayText}}</h3>
    <!--two way data binding-->
    <h3>{{twoWayText}}</h3>
    <input type="text" v-model="twoWayText">
  </div>
  <!--<info-comp first-name="hehe" last-name="hehehehe"/>
  <info-comp first-name="hehe1"/>
  <info-comp :object-data='singleObject'/>-->
  <info-comp>
    Hehe I am using slots
  </info-comp>
  <slot-comp>
    <template #slotTitle>
      Card Slot
    </template>
    <template #default>
        <img :src="imgUrl">
    </template>
  </slot-comp>
  <!--Class style binding-->
    <img :src="imgUrl">
    <h4> :class="{hello:check}"</h4>

    <div>
      <h1 v-if="check">The value is true</h1>
      <h1 v-else>The value is false</h1>
      <button @click="change">Change state</button>
    </div>
</template>
<script>

import InfoComp from '../components/InfoComp.vue'
import SlotComp from '../components/SlotComp.vue'

export default {
  data(){
    return {
      counter:0,
      imgUrl: 'https://www.foodiesfeed.com/wp-content/uploads/2023/06/burger-with-melted-cheese.jpg',
      check:true,
      sports:['soccer','netball','volleyball'],
      objects:[
        {message:'Hello There 1', number:1},
        {message:'Hello There 2', number:2},
        {message:'Hello There 3', number:3},
      ],
      singleObject:{
        name: 'Tyra',
        surname: 'Parring',
      },
      oneWayText: 'This is a one way binding',
      twoWayText: 'This is a two way binding',
    }
  },
  components:{
    InfoComp,
    SlotComp,
  },
  methods: {
    decrement(){
      this.counter--
    },
    increment(){
      this.counter++
      },
      change(){
        this.check = !this.check
        }
  }
}
</script>
<style scoped>
    h1{
      color: blue;
    }
    img{
      width: 200px;
      height: 200px;
    }
</style>
