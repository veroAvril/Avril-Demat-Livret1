<template>
  <div>
    <div class="avril-layout">

      <div class="avril-form">
        <Tabs></Tabs>
        <nuxt />
      </div>

      <div class="avril-help-fake">
        <Actions/>
      </div>

    </div>

    <aside class="avril-profile">
      <div class="avril-back">
        <a href="https://mon-diplome-v2.herokuapp.com/">
          <svg xmlns="http://www.w3.org/2000/svg" id="Bold" viewBox="0 0 24 24">
              <title>arrow-left-1</title>
              <path d="M4.5,12a2.3,2.3,0,0,1,.78-1.729L16.432.46a1.847,1.847,0,0,1,2.439,2.773L9.119,11.812a.25.25,0,0,0,0,.376l9.752,8.579a1.847,1.847,0,1,1-2.439,2.773L5.284,13.732A2.31,2.31,0,0,1,4.5,12Z"></path>
          </svg>
        </a>
      </div>
      <div class="avril-avatar">

      </div>
    </aside>

  </div>
</template>

<script>
import _ from 'lodash';
import Actions from '~/components/Actions.vue';
import Tabs from '~/components/Tabs.vue';

  export default {
    components: {
      Actions,
      Tabs
    },
    computed: {
      heures () {
        return this.$store.state.experiences.heures
      },
      remplissage () {
        return this.$store.state.experiences.remplissage
      },
    },
    methods: {
      back: function (event) {
        console.log('back')
      },
      next: function (event) {
        console.log('next')
      }
    },
    mounted() {

    },
    watch: {
      $route (to, from) {
        this.slugIndex = _.findIndex(this.cerfa, ['slug', this.$route.name])
      }
    },
    afterCreated() {

    },
    data: () => ({
      current: 0,
      slugIndex: 0,
      cerfa:[{
        slug: 'experiences',
        title: "Mes expériences",
      },
      {
        slug: 'experiences-fonction',
        title: "Mes formations",
      },
      {
        slug: 'experiences-famille',
        title: "Mes formations",
      },
      {
        slug: 'experiences-status',
        title: "Mes formations",
      },
      {
        slug: 'experiences-periode',
        title: "Mes formations",
      },
      {
        slug: 'experiences-precision',
        title: "Mes formations",
      },
      {
        slug: 'formations',
        title: "Mes formations",
      },
      {
        slug: 'formations-diplome',
        title: "Mes formations",
      },
      {
        slug: 'formations-autre',
        title: "Mes formations",
      },
      {
        slug: 'formations-comparatibilite',
        title: "Mes formations",
      },
      {
        slug: 'formations-certification',
        title: "Mes formations",
      },
      {
        slug: 'formations-rncp',
        title: "Mes formations",
      },
      {
        slug: 'formations-formations',
        title: "Mes formations",
      },
    ],
    })
  }
</script>

<style>
html {
  font-family: 'Nunito Sans', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}
</style>
