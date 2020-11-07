<template>
  <div>
    <v-row>
      <v-col class="text-center">
        <div class="text-h4">{{ blob.display }}</div>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <v-tooltip bottom>
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              class="ma-2"
              outlined
              fab
              color="secondary"
              v-bind="attrs"
              v-on="on"
            >
              <a :href="`/${blob.taxonid}/${blob.idprev}/`"><v-icon>mdi-arrow-left</v-icon></a>
            </v-btn>
          </template>
          <span>Previous</span>
        </v-tooltip>
      </v-col>
      <v-col class="text-center">
        <a :href="`/${blob.taxonid}/`">
          <v-btn text>
            {{ blob.taxonname }}
          </v-btn>
        </a>
      </v-col>
      <v-col class="text-right">
        <v-tooltip bottom>
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              class="ma-2"
              outlined
              fab
              color="secondary"
              v-bind="attrs"
              v-on="on"
            >
              <a :href="`/${blob.taxonid}/${blob.idnext}/`"><v-icon>mdi-arrow-right</v-icon></a>
            </v-btn>
          </template>
          <span>Next</span>
        </v-tooltip>
      </v-col>
    </v-row>

    <div v-if="blob.det">
      <v-row class="ma-4">
        <v-col>
          <div class="text-h5" id="det">Detection map</div>
        </v-col>
      </v-row>
      <v-row class="ma-4">
        <v-col>
          <v-img
            :src="`https://science.abmi.ca/results/reports/2020/images/${blob.taxonid}/${blob.id}/det.png`"
            alt="Detection map"
            contain
            width="33%">
          </v-img>
        </v-col>
      </v-row>
    </div>

    <div v-if="blob.useavailnorth">
      <v-row class="ma-4">
        <v-col>
          <div class="text-h5" id="useavailnorth">Use-availability, north</div>
        </v-col>
      </v-row>
      <v-row class="ma-4">
        <v-col>
          <v-img
            :src="`https://science.abmi.ca/results/reports/2020/images/${blob.taxonid}/${blob.id}/useavail-north.png`"
            alt="Use-availability, north"
            contain
            width="50%">
          </v-img>
        </v-col>
      </v-row>
    </div>

    <div v-if="blob.coefnorth">
      <v-row class="ma-4">
        <v-col>
          <div class="text-h5" id="coefnorth">Land cover associations, north</div>
        </v-col>
      </v-row>
      <v-row class="ma-4">
        <v-col>
          <v-img
            :src="`https://science.abmi.ca/results/reports/2020/images/${blob.taxonid}/${blob.id}/coef-north.png`"
            alt="Land cover associations, north"
            contain>
          </v-img>
        </v-col>
      </v-row>
    </div>

    <div v-if="blob.useavailsouth">
      <v-row class="ma-4">
        <v-col>
          <div class="text-h5" id="useavailsouth">Use-availability, south</div>
        </v-col>
      </v-row>
      <v-row class="ma-4">
        <v-col>
          <v-img
            :src="`https://science.abmi.ca/results/reports/2020/images/${blob.taxonid}/${blob.id}/useavail-south.png`"
            alt="Use-availability, south"
            contain
            width="50%">
          </v-img>
        </v-col>
      </v-row>
    </div>

    <div v-if="blob.coefsouth">
      <v-row class="ma-4">
        <v-col>
          <div class="text-h5" id="coefsouth">Land cover associations, south</div>
        </v-col>
      </v-row>
      <v-row class="ma-4">
        <v-col>
            <v-img
              :src="`https://science.abmi.ca/results/reports/2020/images/${blob.taxonid}/${blob.id}/coef-south.png`"
              alt="Land cover associations, south"
              contain>
            </v-img>
        </v-col>
      </v-row>
      <div v-if="blob.taxonid === 'mammals'">
        <v-row class="ma-4">
          <v-col>
              <v-img
                :src="`https://science.abmi.ca/results/reports/2020/images/${blob.taxonid}/${blob.id}/soilhf2.png`"
                alt="Land cover associations, south"
                contain
                width="50%">
              </v-img>
          </v-col>
        </v-row>
      </div>
    </div>




  </div>
</template>
<script>
export default {
  name: 'Spp',
  props: ['blob']
}
</script>
