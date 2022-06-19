<template>
  <v-app>

    <v-navigation-drawer app v-model="drawer" :clipped="$vuetify.breakpoint.lgAndUp">
      <v-list>



        <v-list-item :to="{ path: '/' }">
          <v-list-item-icon>
            <v-icon>mdi-home-outline</v-icon>
          </v-list-item-icon>
          <v-list-item-title>Inicio</v-list-item-title>
        </v-list-item>



        <v-list-group :value="true" prepend-icon="mdi-account-multiple-outline">
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title>Pacientes</v-list-item-title>
            </v-list-item-content>
          </template>

          <v-list-item :to="{ name: 'people' }">
            <v-list-item-title>Listado</v-list-item-title>
            <v-list-item-icon>
              <v-icon>mdi-format-list-bulleted</v-icon>
            </v-list-item-icon>
          </v-list-item>
          <v-list-item :to="{ name: 'people-new' }">
            <v-list-item-title>Nuevo paciente</v-list-item-title>
            <v-list-item-icon>
              <v-icon>mdi-account-multiple-plus-outline</v-icon>
            </v-list-item-icon>
          </v-list-item>

        </v-list-group>







        <v-list-item :to="{ name: 'calculator' }">
          <v-list-item-icon>
            <v-icon>mdi-calculator-variant-outline</v-icon>
          </v-list-item-icon>
          <v-list-item-title>Calculadora TMB</v-list-item-title>

        </v-list-item>


      </v-list>

    </v-navigation-drawer>

    <v-app-bar app :clipped-left="$vuetify.breakpoint.lgAndUp">
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title v-text="title"></v-toolbar-title>
    </v-app-bar>


    <v-main>
      <Nuxt />
    </v-main>

    <v-footer>
      <v-row justify="center" no-gutters>
        <v-btn color="primary" small icon>
          <v-icon>mdi-github</v-icon>
        </v-btn>
        <v-btn color="primary" small icon>
          <v-icon>mdi-web</v-icon>
        </v-btn>
        <v-col class="text-center primary--text" cols="12">
          CC {{ new Date().getFullYear() }} - Pedro Pérez
        </v-col>
      </v-row>
    </v-footer>

  </v-app>






</template>

<script>
export default {
  name: 'DefaultLayout',
  data() {
    return {
      drawer: false,
      title: "DIETAPP"
    }
  },
}
</script>
