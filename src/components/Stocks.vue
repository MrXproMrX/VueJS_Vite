<template>

  <div v-if="lindeg" class="mrx_pro_max">
        <section>
      <div class="loader">
        <div class="dot" style="--i:0;"></div>
        <div class="dot" style="--i:1;"></div>
        <div class="dot" style="--i:2;"></div>
        <div class="dot" style="--i:3;"></div>
        <div class="dot" style="--i:4;"></div>
        <div class="dot" style="--i:5;"></div>
        <div class="dot" style="--i:6;"></div>
        <div class="dot" style="--i:7;"></div>
        <div class="dot" style="--i:8;"></div>
        <div class="dot" style="--i:9;"></div>
      </div>
      <h2>Loading...</h2>
      <div class="loader">
        <div class="dot" style="--i:0;"></div>
        <div class="dot" style="--i:1;"></div>
        <div class="dot" style="--i:2;"></div>
        <div class="dot" style="--i:3;"></div>
        <div class="dot" style="--i:4;"></div>
        <div class="dot" style="--i:5;"></div>
        <div class="dot" style="--i:6;"></div>
        <div class="dot" style="--i:7;"></div>
        <div class="dot" style="--i:8;"></div>
        <div class="dot" style="--i:9;"></div>
      </div>
        </section>
  </div>
      
  <H3>Get Info</H3>
  <select v-model="selected">
    <option value="" disabled>Select Company</option>
    <option v-for="value in stock" :key="value.stock" :value="value">{{value.title}}</option>
  </select>
  
  
  <div class="info">
      <div class="info__item">
        <div class="info__img">
          <img :src="selected.url" :alt="selected.title">
        </div>
        <h2 class="info__title">{{selected.title}}</h2>
      </div>
  </div>


  <div class="stock">
    <div class="stock-item" v-for="value in stock" :key="value.id">
      <div class="stock-item_info">
        <div class="stock-item_cover">
          <img :src="value.url" :alt="value.title">
        </div>
        <h3 class="stock-item_title">
          {{value.title}}
          <span>{{value.id}}</span>
        </h3>
      </div>
      <span class="stock-item_price">{{value.id}}</span>
    </div>
  </div>

</template>



<script>
import axios from 'axios';

export default{
  name:'Stocks',
  data(){
    return{
      stock:[],
      errors:[],
      selected:'',

      lindeg:true
    }
  },

  created(){
    axios.get('https://jsonplaceholder.typicode.com/photos')
    .then(responce =>{
      this.stock = responce.data
      console.log(responce)
      this.lindeg = false
    }).catch(e =>{
      this.errors.push(e)
    })

  },
}
</script>