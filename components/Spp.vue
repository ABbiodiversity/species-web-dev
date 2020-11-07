<template>
<div>
    <v-btn
            v-scroll="onScroll"
            v-show="fab"
            fab
            dark
            fixed
            bottom
            right
            color="primary"
            @click="toTop"
          >
            <v-icon>mdi-chevron-up</v-icon>
    </v-btn>
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
              :href="`/${blob.taxonid}/${blob.idprev}/`"
            >
              <v-icon>mdi-chevron-left</v-icon>
            </v-btn>
          </template>
          <span>Previous</span>
        </v-tooltip>
      </v-col>
      <v-col class="text-center">
        <v-btn
          text
          :href="`/${blob.taxonid}/`"
          color="secondary"
        >
          {{ blob.taxonname }}
        </v-btn>
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
              :href="`/${blob.taxonid}/${blob.idnext}/`"
            >
              <v-icon>mdi-chevron-right</v-icon>
            </v-btn>
          </template>
          <span>Next</span>
        </v-tooltip>
      </v-col>
    </v-row>

    <!-- this is always true -->
    <!-- <div v-if="blob.det">  -->
    <v-row>
    <v-col cols="8">

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
            width="50%">
          </v-img>
        </v-col>
      </v-row>

    </v-col>
    <v-col>

  <v-card
    class="mx-auto"
    max-width="300"
    tile
  >
    <v-list>
      <v-subheader>TABLE OF CONTENTS</v-subheader>
      <v-list-item-group
        color="accent"
      >

        <v-list-item href="#det">
          <v-list-item-icon><v-icon>mdi-chart-bubble</v-icon></v-list-item-icon>
          <v-list-item-content><v-list-item-title>
            Detections
          </v-list-item-title></v-list-item-content>
        </v-list-item>

        <div v-if="blob.useavailnorth">
        <v-list-item href="#useavailnorth">
          <v-list-item-icon><v-icon>mdi-pine-tree-fire</v-icon></v-list-item-icon>
          <v-list-item-content><v-list-item-title>
            North
          </v-list-item-title></v-list-item-content>
        </v-list-item>
        </div>
        <div v-if="blob.coefnorth">
        <v-list-item href="#coefnorth">
          <v-list-item-icon><v-icon>mdi-pine-tree-fire</v-icon></v-list-item-icon>
          <v-list-item-content><v-list-item-title>
            North
          </v-list-item-title></v-list-item-content>
        </v-list-item>
        </div>

        <div v-if="blob.useavailsouth">
        <v-list-item href="#useavailsouth">
          <v-list-item-icon><v-icon>mdi-tractor</v-icon></v-list-item-icon>
          <v-list-item-content><v-list-item-title>
            South
          </v-list-item-title></v-list-item-content>
        </v-list-item>
        </div>
        <div v-if="blob.coefsouth">
        <v-list-item href="#coefsouth">
          <v-list-item-icon><v-icon>mdi-tractor</v-icon></v-list-item-icon>
          <v-list-item-content><v-list-item-title>
            South
          </v-list-item-title></v-list-item-content>
        </v-list-item>
        </div>

        <div v-if="blob.sectornorth">
        <v-list-item href="#sectornorth">
          <v-list-item-icon><v-icon>mdi-factory</v-icon></v-list-item-icon>
          <v-list-item-content><v-list-item-title>
            Sectors
          </v-list-item-title></v-list-item-content>
        </v-list-item>
        </div>
        <div v-if="!blob.sectornorth && blob.sectorsouth">
        <v-list-item href="#sectorsouth">
          <v-list-item-icon><v-icon>mdi-factory</v-icon></v-list-item-icon>
          <v-list-item-content><v-list-item-title>
            Sectors
          </v-list-item-title></v-list-item-content>
        </v-list-item>
        </div>

        <div v-if="blob.map">
        <v-list-item href="#map">
          <v-list-item-icon><v-icon>mdi-chart-sankey</v-icon></v-list-item-icon>
          <v-list-item-content><v-list-item-title>
            Predictions
          </v-list-item-title></v-list-item-content>
        </v-list-item>
        </div>

      </v-list-item-group>
    </v-list>
  </v-card>

    </v-col>
    </v-row>


    <!-- </div> -->

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

    <div v-if="blob.sectornorth">
      <v-row class="ma-4">
        <v-col>
          <div class="text-h5" id="sectornorth">Sector effects, north</div>
        </v-col>
      </v-row>
      <v-row class="ma-4">
        <v-col>
          <v-img
            :src="`https://science.abmi.ca/results/reports/2020/images/${blob.taxonid}/${blob.id}/sector-north.png`"
            alt="Sector effects, north"
            contain>
          </v-img>
        </v-col>
      </v-row>
    </div>

    <div v-if="blob.sectorsouth">
      <v-row class="ma-4">
        <v-col>
          <div class="text-h5" id="sectorsouth">Sector effects, south</div>
        </v-col>
      </v-row>
      <v-row class="ma-4">
        <v-col>
          <v-img
            :src="`https://science.abmi.ca/results/reports/2020/images/${blob.taxonid}/${blob.id}/sector-south.png`"
            alt="Sector effects, south"
            contain>
          </v-img>
        </v-col>
      </v-row>
    </div>

    <div v-if="blob.map">
      <v-row class="ma-4">
        <v-col>
          <div class="text-h5" id="map">Predictive map</div>
        </v-col>
      </v-row>
      <v-row class="ma-4">
        <v-col>
          <div v-if="blob.taxonid === 'mammals'">
            This is the <strong>approximate</strong> prediction...
          </div>
          <v-img
            :src="`https://science.abmi.ca/results/reports/2020/images/${blob.taxonid}/${blob.id}/map.png`"
            alt="Detection map"
            contain>
          </v-img>
        </v-col>
      </v-row>
      <div v-if="blob.taxonid === 'mammals'">
        This is the <strong>exact</strong> prediction...
          <v-img
            :src="`https://science.abmi.ca/results/reports/2020/images/${blob.taxonid}/${blob.id}/map2s.png`"
            alt="Detection map"
            contain>
          </v-img>
      </div>
    </div>

</div>
</template>
<script>
export default {
  name: 'Spp',
  props: ['blob'],
  data: () => ({
    fab: false
  }),
  methods: {
    onScroll (e) {
      if (typeof window === 'undefined') return
      const top = window.pageYOffset ||   e.target.scrollTop || 0
      this.fab = top > 20
    },
    toTop () {
      this.$vuetify.goTo(0)
    }
  }
}
</script>
