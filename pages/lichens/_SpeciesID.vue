<template>
  <div>
    <nav class="level">
      <div class="level-left">
        <p class="level-item"><a v-bind:href="'/'+ group + '/' + data.sppprevious">Previous</a></p>
      </div>
      <div class="level-item has-text-centered">
        <div>
        <p class="heading">{{ Group }}</p>
        <p class="level-item title">{{ data.DisplayName }}</p>
        </div>
      </div>
      <div class="level-right">
        <p class="level-item"><a v-bind:href="'/'+ group + '/' + data.sppnext">Next</a></p>
      </div>
    </nav>
    <nav class="level">
      <div class="level-item">
        <p class="level-item">{{ data.Comments }}</p>
      </div>
    </nav>

    <div v-if="data.det">
      <h2 class="subtitle is-size-4">Detection map</h2>
      <div class="columns">
      <div class="column is-one-third">
        <figure class="image">
          <img id="det" 
            v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/' + data.SpeciesID + '-det.png'"
            alt="Detection map" />
        </figure>
      </div>
    </div>
  </div>

  <div v-if="data['coef-north']">
    <h2 class="subtitle is-size-4">Coefficients, north</h2>
    <figure class="image">
      <img id="det" 
        v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/' + data.SpeciesID + '-coef-north.png'"
        alt="Coefficients, north" />
    </figure>
  </div>
  <div v-else>
    <div v-if="data['useavail-north']">
      <h2 class="subtitle is-size-4">Use-availability, north</h2>
      <div class="columns">
        <div class="column is-two-thirds">
          <figure class="image">
            <img id="det" 
              v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/' + data.SpeciesID + '-useavail-north.png'"
              alt="Use-availability, north" />
          </figure>
        </div>
      </div>
    </div>
  </div>


  <div v-if="data['coef-south']">
    <h2 class="subtitle is-size-4">Coefficients, south</h2>
    <figure class="image">
      <img id="det" 
        v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/' + data.SpeciesID + '-coef-south.png'"
        alt="Coefficients, south" />
    </figure>
  </div>
  <div v-else>
    <div v-if="data['useavail-south']">
      <h2 class="subtitle is-size-4">Use-availability, south</h2>
      <div class="columns">
        <div class="column is-two-thirds">
          <figure class="image">
            <img id="det" 
              v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/' + data.SpeciesID + '-useavail-south.png'"
              alt="Use-availability, south" />
          </figure>
        </div>
      </div>
    </div>
  </div>

    <div v-if="data.map">
      <h2 class="subtitle is-size-4">Relative abundance maps</h2>
        <figure class="image">
          <img id="det" 
            v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/' + data.SpeciesID + '-map.png'"
            alt="Relative abundance maps" />
        </figure>
  </div>

  <div v-if="data['sector-north']">
    <h2 class="subtitle is-size-4">Sector effects, north</h2>
    <figure class="image">
      <img id="det" 
        v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/' + data.SpeciesID + '-sector-north.png'"
        alt="Sector effects, north" />
    </figure>
  </div>


  <div v-if="data['sector-south']">
    <h2 class="subtitle is-size-4">Sector effects, south</h2>
    <figure class="image">
      <img id="det" 
        v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/' + data.SpeciesID + '-sector-south.png'"
        alt="Sector effects, south" />
    </figure>
  </div>

  </div>
</template>
<script>
const group = 'lichens'
const Group = 'Lichens'
import axios from 'axios'

export default {

  head () {
    return {
      title: this.data.DisplayName
    }
  },
  data () {
    return { group: group, Group: Group}
  },
  asyncData ({ params }) {
    return axios.get(`http://sc-dev.abmi.ca/reports/2018/api/${group}/${params.SpeciesID}/index.json`)
    .then((res) => {
      return { 
        data: res.data
      }
    })
    .catch((e) => {
      error({ statusCode: 404, message: 'Data not found' })
    })
  }

}

</script>
