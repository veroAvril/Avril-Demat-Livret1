<template>
  <div class="form">

    <div class="field" v-if="slugIndex == 0" style="margin-right:3rem">
      <div class="control">
        <nuxt-link to="/recapitulatif" class="is-ok button is-dark is-pulled-right">
          Enregistrer mon livret de recevabilité
        </nuxt-link>
        <!-- <nuxt-link to="/experiences/fonction" class="is-ok button is-default is-pulled-right" style="margin-right:1rem">
        Ajouter une nouvelle expérience
      </nuxt-link> -->
    </div>
  </div>

    <p>TODO : ajouter un message pour cloturer le livret 1, l'envoyer ou l'enregistrer pour remplir plus tard</p>
    <p>Tout ça seulement si le taux de remplissage est suffisant</p>

    <div class="form-fields">

        <h1 class="title is-5">Vos expériences professionnelles</h1>

        <nuxt-link to="experiences/fonction" :class="heures<1607 ? 'button is-dark' : 'button'">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
              <title>add</title>
              <path d="M0,12a1.5,1.5,0,0,0,1.5,1.5h8.75a.25.25,0,0,1,.25.25V22.5a1.5,1.5,0,0,0,3,0V13.75a.25.25,0,0,1,.25-.25H22.5a1.5,1.5,0,0,0,0-3H13.75a.25.25,0,0,1-.25-.25V1.5a1.5,1.5,0,0,0-3,0v8.75a.25.25,0,0,1-.25.25H1.5A1.5,1.5,0,0,0,0,12Z"></path>
          </svg>&nbsp; Ajouter une expérience
        </nuxt-link>
        <span class="avril-ou" v-if="heures >= 1607">&nbsp;ou&nbsp;</span>
        <nuxt-link v-if="heures >= 1607" :event="heures < 1607 ? '' : 'click'" to="/formations" class="is-ok button is-dark">
          Avancer vers mes formations
        </nuxt-link>

        <div class="columns is-multiline">
          <div v-for="experience in experiences" class="column is-half">
            <div class="box is-equal-height">
              <h3 class="title is-4">{{ experience.fonction }}</h3>
              <h3 class="title is-6">{{ experience.duree }} heures</h3>
              <p>{{ experience.entreprise }}</p>
              <span>{{ experience.periode }}</span>
              <a href="#">éditer</a>
            </div>
          </div>
          <div class="column is-one-quarter">
            <div class="avril__box__experience is-equal-height">
            </div>
          </div>
        </div>

      </div>


      <div class="form-help">
        <h3 class="title is-4">Besoin d'aide ?</h3>
        <div class="form-help-content">
          Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
        </div>
        <p style="margin-top:1rem">
          <a href="#" class="is-text">J'ai besoin de plus d'aide</a>
        </p>
      </div>
    </div>
</template>

<script>
// import Logo from '~/components/Logo.vue'
// const ioHook = require('iohook');
export default {
  layout: 'experience',
  components: {
    // Logo
  },
  computed: {
    experiences () {
      return this.$store.state.experiences.experiences
    },
    heures () {
      return this.$store.state.experiences.heures
    },
    pourcentage () {
      if( (this.$store.state.experiences.heures*100)/1607 > 100 )
        return 100
      else
        return (this.$store.state.experiences.heures*100)/1607
    }
  },

  created() {
    // console.log('accueil created')
  },

  mounted() {
    // this.$refs.avril__name.focus()
    this.$store.commit('application/disableExperienceStepper')
    this.$store.commit('application/disableFormationStepper')
    this.$store.commit('application/changeTab', 0)
  },
  methods: {
    keymonitor: function(event) {
      if(event.key == "Enter")
      {
        this.$router.push('name')
      }
    }
  },
  watch: {
    $route (to, from) {
      this.slugIndex = _.findIndex(this.cerfa, ['slug', this.$route.name])
    }
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
.avril-ou{
  margin-top: 8px;
  display: inline-block;
}
.columns.is-multiline{
  margin-top: 40px;
}
.avril__ajouter__experience {
  display: block
}
.is-equal-height {
   display: flex;
   flex-direction: column;
   height: 100%;
}
</style>
