<template>
  <q-page class="flex flex-center">
    <!--<img alt="Quasar logo" src="~assets/quasar-logo-full.svg">-->
    <div>
      <ul>
        <li v-for="(children,index) in childrens" :key="index">
          {{children.kind}}
        </li>
      </ul>
    </div>
  </q-page>
</template>

<style>
</style>

<script>
import axios from 'axios'
export default {
  data (){
    return {
      childrens: []
    }
  },
  name: 'PageIndex',
  created () {
    this.prueba()
  },
  methods: {
    async prueba () {
      try{
        var le = await axios.get('https://www.reddit.com/r/aww.json?raw_json=1')
        console.log(le.data.data.children)
        this.childrens = le.data.data.children
      }
      catch(e){
      }
    }
  }
}
</script>
