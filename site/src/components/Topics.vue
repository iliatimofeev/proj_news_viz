<template>
  <v-container fluid >

    <v-layout
      row wrap
    >
        <v-flex d-flex xs11 class="px-1">
          <v-card  xs12 >
            <v-card-title primary-title>
              <div class="title">Топик</div>

            </v-card-title>
            <v-responsive class="px-4 mx-auto" >
    <vega-chart  :spec="require('../assets/charts/topics_main.vg.json')" class="mx-auto">
    </vega-chart>

            </v-responsive>
            <v-card-text>
            <div class="subheading">
              <span>Данные "лента": <a href="https://www.kaggle.com/yutkin/corpus-of-russian-news-articles-from-lenta"> источник</a> </span>
                         <v-divider
      class="mx-3"
      vertical
    ></v-divider>
              <span>Модель "bigARTM Baseline": <a href="https://github.com/ods-ai-ml4sg/proj_news_viz/blob/master/nlp/topic_models/bigARTM%20Baseline.ipynb"> искодник</a> </span>
               </div>
   
            </v-card-text>
          </v-card>
        </v-flex>

 

    </v-layout>
  </v-container>
</template>

<script>
import Vue from "vue";
import Vega from "@/components/Vega.vue";

Vue.component(Vega.name, Vega);

export default {
  data: () => ({})
};
</script>

<style>
</style>
