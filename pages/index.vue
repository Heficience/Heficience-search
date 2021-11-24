<template>
  <section class="section">
  <div class="container">
    <div class="columns">
      <div class="column ">
        <div class="box ">
          <h1 class="title">Rechercher sur <select  @change="currentEngine = parseInt($event.target.value); console.log(currentEngine)">
            <option value="0" selected>Defaut : {{searchEngines[0].name}}</option>
            <option v-for="(engine,i) in searchEngines" value="i" :key="'se-'+i"  :selected="currentEngine == i">{{engine.name}}</option>
            </select></h1>
  
          <div class="field has-addons">
              <div class="control" :class="loading ? 'is-loading' :''" >
                <input type="text" class="input is-large is-primary" v-model="search" @change="suggests = []" @keydown.down="onArrow" @keydown.up="onArrow" v-on:keyup.enter="openGoogle()" @input="searchbar()" :placeholder="'Rechercher'">
                <ul v-if="suggests.length > 0" class="suggests">
              <li v-for="(suggest, i) in suggests">
                <a target="_blank" @click="openGoogle(suggest)" :class="{'has-text-weight-bold': index == i}">
                  {{ suggest }}
                </a>
              </li>
            </ul>
              </div>
  
         
              <div class="control">
                <a target="_blank" :href="'https://www.google.com/search?q=' + search">
                    <button class="button is-primary is-large">
                      Rechercher
                    </button>
                </a>
              </div>
              
          </div>
          

        </div>

       
      </div>
    </div>
  </div>
  <hr/>
    <div class="columns is-desktop ">
      <div v-for="link in links" class="column box m-5 has-text-centered is-centered">
        <a  :href="link.url" class=" is-flex is-flex-direction-column">
        <div class="is-align-self-center">
         <figure class="image is-128x128">
          <img :src="link.icon">
        </figure>
    
          </div>
          <h1 class="title is-4">{{ link.name }}</h1>


        </a>
        </div>
      </div>

    
  </section>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HomePage',
  data () {
    return {
      search: '',
      suggests: [],
      index: -1,
      currentEngine: 0,
      loading : true,
      cors : 'https://cors-any.herokuapp.com/',
      links : [
        {
          name : 'Facebook',
          url : 'https://www.facebook.com/',
          icon : 'https://upload.wikimedia.org/wikipedia/commons/thumb/c/cd/Facebook_logo_%28square%29.png/600px-Facebook_logo_%28square%29.png'
        },
        {
          name : 'Instagram',
          url : 'https://www.instagram.com/',
          icon : 'https://upload.wikimedia.org/wikipedia/commons/thumb/e/e7/Instagram_logo_2016.svg/langfr-220px-Instagram_logo_2016.svg.png'
        },
        {
          name : 'Twitter',
          url : 'https://www.twitter.com/',
          icon : 'https://media.discordapp.net/attachments/899757615083552791/909538632258445353/580b57fcd9996e24bc43c53e.png'
        },
        {
          name : 'Youtube',
          url : 'https://www.youtube.com/',
          icon : 'https://upload.wikimedia.org/wikipedia/commons/7/72/YouTube_social_white_square_%282017%29.svg'
        }
      
      ],
      searchEngines : [
        {
          name : 'Google',
          url : 'https://www.google.com/search?q=',
          url_api: 'https://suggestqueries.google.com/complete/search?client=firefox&q=',
          icon : 'https://upload.wikimedia.org/wikipedia/commons/thumb/2/2c/Google_2015_logo.svg/1200px-Google_2015_logo.svg.png'
        },
        
        {
          name : 'Yahoo',
          url : 'https://fr.search.yahoo.com/search?p=',
          url_api: 'https://search.yahoo.com/sugg/ff/g?output=fxjson&command=',
        },
        {
          name : 'Bing',
          url : 'https://www.bing.com/search?q=',
          url_api: 'https://api.bing.com/osjson.aspx?query=',
        },
        {
          name : 'DuckDuckGo',
          url : 'https://duckduckgo.com/?q=',
          url_api: 'https://duckduckgo.com/ac/?q=',
        },
        {
          name : 'Wikipedia',
          url : 'https://fr.wikipedia.org/wiki/',
          url_api: 'https://fr.wikipedia.org/w/api.php?action=opensearch&search=',
        }
      ]
    }
  },
  methods: {
    searchbar () {
      this.index = -1
      if(this.search == "") {
        this.suggests = []
        return
      }
      this.loading = true
      this.search = this.search.replace(/ /g, '+')
      console.log(this.searchEngines[this.currentEngine].url_api )
      axios.get(this.cors+this.searchEngines[this.currentEngine].url_api + this.search, {
        params: {
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
        this.loading = false
          
      })
    },
    openGoogle (thesearch = this.search) {
      thesearch = thesearch.replace(/ /g, '+')
      window.open('https://www.google.com/search?q=' +  thesearch)
      this.search = ""
      this.suggests = []
      this.index = 0

    },
    onArrow (e) {
      if(e.keyCode == 40) {
        this.index++
        if(this.index == this.suggests.length) {
          this.index = 0
        }
      } else if(e.keyCode == 38) {
        this.index--
        if(this.index == -1) {
          this.index = this.suggests.length - 1
        }
      }
      this.search = this.suggests[this.index]
    }
  },
  mounted () {
    // Reveil du service cors pour les requêtes cross-domain
    fetch(this.cors).then(response => {
      this.loading = false
    })
  }


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
[v-cloak] {
  display: none;
}
</style>
