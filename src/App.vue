<template>
  <div id="app">
    <nav class="navbar navbar-default">
      <div class="container-fluid">
        <ul class="nav navbar-nav">
          <li>
            <router-link to="/">Evaluation</router-link>
          </li>
          <li>
            <router-link to="/feedback">Feedback(for writting)</router-link>
          </li>
           <li>
            <router-link to="/details">Feedback(for reading)</router-link>
          </li>
          <!-- <li>
            <router-link to="/creator">SurveyJS Creator</router-link>
          </li>
          <li>
            <router-link to="/exportpdf">PDF Export</router-link>
          </li>
          <li>
            <router-link to="/analytics">Analytics</router-link>
          </li>
          <li>
            <router-link to="/analyticstabulator">Results Table</router-link>
          </li>
          <li>
            <router-link to="/analyticsdatatables"
              >Results Table (IE Support)</router-link
            >
          </li> -->
         </ul>
      </div>
    </nav>
    <router-view class="view"></router-view>
  </div>
</template>

<script>
import Vue from "vue";
import VueRouter from "vue-router";
import Oruga from '@oruga-ui/oruga'

import "bootstrap/dist/css/bootstrap.css";
import '@oruga-ui/oruga/dist/oruga.css'

Vue.use(Oruga);
Vue.use(VueRouter);

const Evaluation = () => import("./views/Evaluation.vue");
const Feedback = () =>
  import(/* webpackChunkName: "survey" */ "./views/Feedback.vue");
  const Details = () =>
  import(/* webpackChunkName: "survey" */ "./views/Details.vue");
const Creator = () =>
  import(/* webpackChunkName: "creator" */ "./views/Creator.vue");
const ExportToPDF = () =>
  import(/* webpackChunkName: "creator" */ "./views/ExportToPDF.vue");
const Analytics = () =>
  import(/* webpackChunkName: "creator" */ "./views/Analytics.vue");
const AnalyticsTabulator = () =>
  import(/* webpackChunkName: "creator" */ "./views/AnalyticsTabulator.vue");
const AnalyticsDatatables = () =>
  import(/* webpackChunkName: "creator" */ "./views/AnalyticsDatatables.vue");

const router = new VueRouter({
  mode: "history",
  base: __dirname,
  routes: [
    { path: "/", component: Evaluation },
    // Just use them normally in the route config
    { path: "/feedback", component: Feedback },
    // multiple parameters, `/` should not be encoded. The name is also important
    // https://github.com/vuejs/vue-router/issues/2719
    // { path: '/a/:tags*', name: 'tagged', component: () => new Promise(resolve => {
    //   setTimeout(() => {
    //     resolve({
    //       template: `<div>
    //         <h2>Lazy with params</h2>
    //         <pre id="tagged-path">{{ $route.path }}</pre>
    //       </div>`
    //     })
    //   }, 200)
    // }) },
    // Bar and Baz belong to the same root route
    // and grouped in the same async chunk.
    { path: "/creator", component: Creator },
    { path: "/exportpdf", component: ExportToPDF },
    { path: "/analytics", component: Analytics },
    { path: "/analyticstabulator", component: AnalyticsTabulator },
    { path: "/analyticsdatatables", component: AnalyticsDatatables },
    { path: "/details", component: Details },

  ],
});

export default {
  name: "app",
  router: router,
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
