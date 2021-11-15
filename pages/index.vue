<template>
  <section class="section">
  <div class="container">
    <div class="columns">
      <div class="column is-half ">
        <div class="box">
          <h1 class="title"> Rechercher sur Google </h1>
          <p class="subtitle">
            <input type="text" class="input" v-model="search" @change="suggests = []" @keydown.down="onArrow" @keydown.up="onArrow" v-on:keyup.enter="openGoogle()" @input="searchGoogle()" placeholder="Rechercher sur Google">
            <ul v-if="suggests.length > 0" class="suggests">
              <li v-for="suggest in suggests">
                <a target="_blank" :href="'https://www.google.com/search?q=' + suggest">
                  {{ suggest }}
                </a>
              </li>
            </ul>
          </p>
            
          <a target="_blank" :href="'https://www.google.com/search?q=' + search">
              <button class="button is-primary">
                Rechercher
              </button>
          </a>
        
        </div>

       
      </div>
    </div>
  </div>
    <div class="columns is-mobile">
        <a class="box  m-5" href="https://www.facebook.com/">
          <figure class="image is-128x128"> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/cd/Facebook_logo_%28square%29.png/600px-Facebook_logo_%28square%29.png" alt="">
          </figure>
          
          <div class="content mt-2">
            <p class="title is-4">Facebook</p>
          </div>
        </a>

        <a class="box  m-5" href="https://www.instagram.com/">
          <figure class="image is-128x128"> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e7/Instagram_logo_2016.svg/langfr-220px-Instagram_logo_2016.svg.png" alt="">
          </figure>

          <div class="content mt-2">
            <p class="title is-4">Instagram</p>
          </div>

        </a>

        <a class="box m-5" href="https://www.twitter.com/">
          <figure class="image is-128x128"> <img src="https://media.discordapp.net/attachments/899757615083552791/909538632258445353/580b57fcd9996e24bc43c53e.png" alt="">
          </figure>

          <div class="content mt-2">
            <p class="title is-4">Twitter</p>
          </div>

        </a>

        <a class="box m-5" href="https://www.youtube.com/">
          <figure class="image is-128x128"> <img src="https://upload.wikimedia.org/wikipedia/commons/7/72/YouTube_social_white_square_%282017%29.svg" alt="">
          </figure>

          <div class="content mt-2">
            <p class="title is-4">Youtube</p>
          </div>
        </a>
      </div>

    
  </section>
</template>

<script>
import Card from '~/components/Card'
import axios from 'axios'
export default {
  name: 'HomePage',
  data () {
    return {
      search: '',
      suggests: [],
      index: 0
    }
  },
  methods: {
    searchGoogle () {
      if(this.search == "") {
        this.suggests = []
        return
      }
      axios.get('https://cors--any.herokuapp.com/http://clients1.google.com/complete/search', {
        params: {
          q: this.search,
          client: 'firefox',
          hl: 'fr'
        }
      })
      .then(response => {
        if(this.search == "") {
          this.suggests = []
          return
        }
        this.suggests = response.data[1]
          
      })
    },
    openGoogle () {
      window.open('https://www.google.com/search?q=' + this.search)
    },
    onArrow (e) {
      if(e.keyCode == 40) {
        this.index++
        if(this.index >= this.suggests.length) {
          this.index = 0
        }
        this.search = this.suggests[this.index]
      }
      if(e.keyCode == 38) {
        this.index--
        if(this.index < 0) {
          this.index = this.suggests.length - 1
        }
        this.search = this.suggests[this.index]
      }
    }
  },


}
</script>

<style>
.suggests {
  position: absolute;
  z-index: 1;
  background: #fff;
  border: 1px solid #ddd;
  border-top: none;
  border-radius: 0 0 4px 4px;
  box-shadow: 0 1px 2px rgba(0,0,0,.1);
  padding: 10px;
}
</style>
