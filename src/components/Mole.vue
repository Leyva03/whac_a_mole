<template>
  <div class="moleHole" @click="hitMole"><img :src="currentImage"></div>

</template>

<script>
import empty from "../empty.png" 
import mole from "../mole.png"
import ouch from "../ouch.png"
export default {
  name: 'Mole',
  data(){
    return{
      currentImage: empty,
      hit: false
    }
  },
  methods:{
    hitMole(){
      if(this.currentImage==mole){
        this.currentImage = ouch
        this.hit = true
      }
    },
    showMole(){
      this.currentImage = mole
      setTimeout(()=>{
        if(!this.hit){
          this.hideMole()
        }
        
      }, Math.random() * 1000 + 500)
    },
    hideMole(){
      this.currentImage = empty
      setTimeout(()=>{
        if(!this.hit){
          this.showMole()
        }
      }, Math.random() * 1000 + 500)
    }

  },
  mounted(){
    this.showMole()
  }
  
};
</script>
