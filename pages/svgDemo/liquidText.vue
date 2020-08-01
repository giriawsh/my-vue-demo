<template>
  <v-container class="grey lighten-5 container" fluid>
    <v-row>
      <v-col
        v-for="n in 3"
        :key="n"
        cols="6"
        md="4"
      >
        <v-card
          class="pa-2"
          outlined
          tile
          v-if="n === 1"
        >
          <v-system-bar lights-out></v-system-bar>
          <v-carousel
            :continuous="false"
            :cycle="true"
            :show-arrows="false"
            hide-delimiter-background
            delimiter-icon="mdi-minus"
            height="300"
          >
            <v-carousel-item
              v-for="i in 2"
              :key="i"
            >
              <v-sheet
                height="100%"
                tile
                v-if="i === 1"
              >
                <v-row
                  class="fill-height"
                  align="center"
                  justify="center"
                >
                  <!--                  <div class="display-3">{{ slide }} Slide</div>-->
                  <svg class="mySvg" xmlns="http://www.w3.org/2000/svg">
                    <filter id="filter_1">
                      <feTurbulence id="turbulence_1" type="turbulence" baseFrequency="0.01" numOctaves="1"
                                    seed="1"/>
                      <feDisplacementMap id="displacement_map_1" in="SourceGraphic" in2="turbulence" scale="0"
                                         xChannelSelector="R" yChannelSelector="B"/>
                    </filter>
                    <filter id="filter_2">
                      <feTurbulence id="turbulence_2" type="turbulence" baseFrequency="0.01" numOctaves="1"
                                    seed="1"/>
                      <feDisplacementMap id="displacement_map_2" in="SourceGraphic" in2="turbulence" scale="0"
                                         xChannelSelector="R" yChannelSelector="B"/>
                    </filter>
                    <filter id="filter_3">
                      <feTurbulence id="turbulence_3" type="turbulence" baseFrequency="0.01" numOctaves="1"
                                    seed="1"/>
                      <feDisplacementMap id="displacement_map_3" in="SourceGraphic" in2="turbulence" scale="0"
                                         xChannelSelector="R" yChannelSelector="B"/>
                    </filter>
                  </svg>
                  <div class="water water_1">water</div>
                  <div class="water water_2">water</div>
                  <div class="water water_3" v-on:click="waterClick">water</div>
                </v-row>
              </v-sheet>
              <v-sheet
                height="100%"
                tile
                v-if="i === 2"
              >
                <v-row
                  class="fill-height"
                  align="center"
                  justify="center"
                >
                  <!--                  <div class="display-3">{{ slide }} Slide</div>-->
                  <svg class="mySvg" xmlns="http://www.w3.org/2000/svg">
                    <filter id="filter_4">
                      <feTurbulence id="turbulence_4" type="turbulence" baseFrequency="0.01" numOctaves="1"
                                    seed="1"/>
                      <feDisplacementMap id="displacement_map_4" in="SourceGraphic" in2="turbulence" scale="0"
                                         xChannelSelector="R" yChannelSelector="B"/>
                    </filter>
                    <filter id="filter_5">
                      <feTurbulence id="turbulence_5" type="turbulence" baseFrequency="0.01" numOctaves="1"
                                    seed="1"/>
                      <feDisplacementMap id="displacement_map_5" in="SourceGraphic" in2="turbulence" scale="0"
                                         xChannelSelector="R" yChannelSelector="B"/>
                    </filter>
                    <filter id="filter_6">
                      <feTurbulence id="turbulence_6" type="turbulence" baseFrequency="0.01" numOctaves="1"
                                    seed="1"/>
                      <feDisplacementMap id="displacement_map_6" in="SourceGraphic" in2="turbulence" scale="0"
                                         xChannelSelector="R" yChannelSelector="B"/>
                    </filter>
                  </svg>
                  <div class="jelly jelly_1">jelly</div>
                  <div class="jelly jelly_2">jelly</div>
                  <div class="jelly jelly_3" v-on:click="jellyClick">jelly</div>
                </v-row>
              </v-sheet>
            </v-carousel-item>
          </v-carousel>
          <v-list two-line>
            <v-list-item>
              <v-list-item-avatar>
                <v-img src="/avatar.png"/>
              </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title>SVG DEMO</v-list-item-title>
                <v-list-item-subtitle>液体字体 果冻字体</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </v-list>
          <!--              </v-card>-->
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
  import anime from 'animejs';

  export default {
    name: "liquidText",
    data() {
      return {
        duration: 2000,
        colors: [
          'green',
          'secondary',
          'yellow darken-4',
          'red lighten-2',
          'orange darken-1',
        ],
        cycle: false,
      }
    },
    mounted() {
      this.water();
      this.duration = 2000;
    },
    methods: {
      water() {
        anime(
          {
            targets: ['#turbulence_1', '#displacement_map_1'],
            baseFrequency: [0.03, 0],
            scale: [20, 0],
            duration: this.duration,
            easing: 'easeOutCubic',
          },
          anime({
            targets: ['#turbulence_2', '#displacement_map_2'],
            baseFrequency: [0.2, 0],
            scale: [20, 0],
            duration: this.duration * 2,
            easing: 'easeOutCubic'
          }),

          anime({
            targets: ['#turbulence_3', '#displacement_map_3'],
            baseFrequency: [0.1, 0],
            scale: [40, 0],
            duration: this.duration * 3,
            easing: 'easeOutCubic'
          })
        )
      },
      jelly() {
        anime(
          {
            targets: ['#turbulence_4', '#displacement_map_4'],
            baseFrequency: [0.03, 0],
            scale: [20, 0],
            duration: this.duration,
            easing: 'easeOutCubic',
          },
          anime({
            targets: ['#turbulence_5', '#displacement_map_5'],
            baseFrequency: [0.02, 0],
            scale: [20, 0],
            duration: this.duration * 2,
            easing: 'easeOutCubic'
          }),

          anime({
            targets: ['#turbulence_6', '#displacement_map_6'],
            baseFrequency: [0.01, 0],
            scale: [20, 0],
            duration: this.duration * 3,
            easing: 'easeOutCubic'
          })
        )
      },
      waterClick() {
        this.water();
        // this.duration = 2000;
        this.duration = 2000;
      },
      jellyClick() {
        this.jelly();
        this.duration = 2000;
      }
    }
  }
</script>
<style scoped>
  .mySvg {
    display: none;
  }

  .water {
    position: absolute;
    /*background: linear-gradient(180deg, #ffffff, #ffffff, #0000ff);*/
    -webkit-background-clip: text;
    text-fill-color: transparent;
    opacity: 0.8;
    cursor: pointer;
    padding-left: 30px;
  }

  .water_1 {
    -webkit-filter: url(#filter_1);
    filter: url(#filter_1);
  }

  .water_2 {
    -webkit-filter: url(#filter_2);
    filter: url(#filter_2);
  }

  .water_3 {
    -webkit-filter: url(#filter_3);
    filter: url(#filter_3);
    opacity: 0.3;
  }

  .jelly {
    position: absolute;
    /*background: linear-gradient(180deg, #ffffff, #ffffff, #0000ff);*/
    -webkit-background-clip: text;
    text-fill-color: transparent;
    opacity: 0.8;
    cursor: pointer;
    padding-left: 30px;
  }

  .jelly_1 {
    -webkit-filter: url(#filter_4);
    filter: url(#filter_4);
  }

  .jelly_2 {
    -webkit-filter: url(#filter_5);
    filter: url(#filter_5);
  }

  .jelly_3 {
    -webkit-filter: url(#filter_6);
    filter: url(#filter_6);
    opacity: 0.3;
  }

  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100vw;
    height: 100vh;
    overflow: hidden;
    background: radial-gradient(ellipse at bottom, #1b2735 0%, #090a0f 100%);
    color: rgba(100, 200, 255, 0.7);
    font-family: 'Dosis', sans-serif;
    font-size: 8rem;
  }
</style>
