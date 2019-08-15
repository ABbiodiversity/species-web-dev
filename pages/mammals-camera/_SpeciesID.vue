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

    <div v-if="data['map-det']">
      <h2 class="subtitle is-size-4">Detection map</h2>
      <div class="columns">
      <div class="column is-one-third">
        <figure class="image">
          <img id="det" 
            v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/map-det/' + data.SpeciesID + '.png'"
            alt="Detection map" />
        </figure>
      </div>
    </div>
  </div>

  <div v-if="data['coef-north-combo']">
    <h2 class="subtitle is-size-4">Coefficients, north</h2>
    <h3 class="subtitle is-size-5">Combo</h3>
    <figure class="image">
      <img  
        v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/coef-north-combo/' + data.SpeciesID + '.png'"
        alt="Combo coefficients, north" />
    </figure>
    <div v-if="data['coef-north-winter']">
      <h3 class="subtitle is-size-5">Winter</h3>
      <figure class="image">
        <img  
          v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/coef-north-winter/' + data.SpeciesID + '.png'"
          alt="Winter coefficients, north" />
      </figure>
    </div>
    <div v-if="data['coef-north-summer']">
      <h3 class="subtitle is-size-5">Summer</h3>
      <figure class="image">
        <img  
          v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/coef-north-summer/' + data.SpeciesID + '.png'"
          alt="Summer coefficients, north" />
      </figure>
    </div>
  </div>
  <div v-else>
    <div v-if="data['useavail-north']">
      <h2 class="subtitle is-size-4">Use-availability, north</h2>
      <div class="columns">
        <div class="column is-two-thirds">
          <figure class="image">
            <img  
              v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/useavail-north/' + data.SpeciesID + '.png'"
              alt="Use-availability, north" />
          </figure>
        </div>
      </div>
    </div>
  </div>

  <div v-if="data['coef-south-combo-nontreed']">
    <h2 class="subtitle is-size-4">Coefficients, south</h2>
    <h3 class="subtitle is-size-5">Combo</h3>
    <figure class="image">
      <img  
        v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/coef-south-combo-nontreed/' + data.SpeciesID + '.png'"
        alt="Combo coefficients, south" />
    </figure>
    <figure class="image">
      <img  
        v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/coef-south-combo-treed/' + data.SpeciesID + '.png'"
        alt="Combo coefficients, south" />
    </figure>
    <div v-if="data['coef-south-winter-nontreed']">
      <h3 class="subtitle is-size-5">Winter</h3>
      <figure class="image">
        <img  
          v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/coef-south-winter-nontreed/' + data.SpeciesID + '.png'"
          alt="Winter coefficients, south, non treed" />
      </figure>
      <figure class="image">
        <img  
          v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/coef-south-winter-treed/' + data.SpeciesID + '.png'"
          alt="Winter coefficients, south, treed" />
      </figure>
    </div>
    <div v-if="data['coef-south-summer-nontreed']">
      <h3 class="subtitle is-size-5">Summer</h3>
      <figure class="image">
        <img  
          v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/coef-south-summer-nontreed/' + data.SpeciesID + '.png'"
          alt="Summer coefficients, south, non treed" />
      </figure>
      <figure class="image">
        <img  
          v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/coef-south-summer-treed/' + data.SpeciesID + '.png'"
          alt="Summer coefficients, south, treed" />
      </figure>
    </div>
  </div>
  <div v-else>
    <div v-if="data['useavail-south']">
      <h2 class="subtitle is-size-4">Use-availability, south</h2>
      <div class="columns">
        <div class="column is-two-thirds">
          <figure class="image">
            <img  
              v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/useavail-south/' + data.SpeciesID + '.png'"
              alt="Use-availability, south" />
          </figure>
        </div>
      </div>
    </div>
  </div>

  <div v-if="data['map-cr']">
    <h2 class="subtitle is-size-4">Relative abundance maps</h2>
    <div class="columns">
      <div class="column is-one-third">
        <figure class="image">
          <img id="det" 
            v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/map-rf/' + data.SpeciesID + '.png'"
            alt="Reference" />
        </figure>
      </div>
      <div class="column is-one-third">
        <figure class="image">
          <img id="det" 
            v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/map-cr/' + data.SpeciesID + '.png'"
            alt="Current" />
        </figure>
      </div>
      <div class="column is-one-third">
        <figure class="image">
          <img id="det" 
            v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/map-df/' + data.SpeciesID + '.png'"
            alt="Difference" />
        </figure>
      </div>

    </div>
  </div>

    <div class="columns">
      <div v-if="data['map-spclim-north']">
        <div class="column is-one-third">
          <figure class="image">
            <img id="det" 
              v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/map-spclim-north/' + data.SpeciesID + '.png'"
              alt="Reference" />
          </figure>
          <p>Space-climate, north</p>
        </div>
      </div>
      <div v-if="data['map-spclim-south']">
        <div class="column is-one-third">
          <figure class="image">
            <img id="det" 
              v-bind:src="'http://sc-dev.abmi.ca/reports/2018/images/' + group + '/map-spclim-south/' + data.SpeciesID + '.png'"
              alt="Reference" />
          </figure>
          <p>Space-climate, south</p>
        </div>
      </div>
    </div>


  </div>
</template>
<script>
const group = 'mammals-camera'
const Group = 'Mammals (Camera)'
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
