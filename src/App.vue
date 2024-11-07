<template>
  <v-app>
    <!-- Barra de Aplicação -->
    <v-app-bar app color="indigo" dark>
      <v-toolbar-title>BBox</v-toolbar-title>
      <v-spacer></v-spacer>

      <v-btn v-show="$vuetify.breakpoint.mdAndUp" text @click="currentSection = 'minha-caixa'">Pontos de Descarte</v-btn>
      <v-btn v-show="$vuetify.breakpoint.mdAndUp" text @click="currentSection = 'itens-point'">Itens Points</v-btn>
      <v-btn v-show="$vuetify.breakpoint.mdAndUp" text @click="currentSection = 'ranking'">Ranking</v-btn>
      <v-btn v-show="$vuetify.breakpoint.mdAndUp" text @click="currentSection = 'metrics'">Métricas</v-btn>

      <v-btn icon v-show="$vuetify.breakpoint.smAndDown" @click="drawer = !drawer">
        <v-icon class="white--text">mdi-menu</v-icon>
      </v-btn>
    </v-app-bar>

    <!-- Drawer (Menu Lateral) para Dispositivos Móveis -->
    <v-navigation-drawer v-model="drawer" temporary app>
      <v-list>
        <v-list-item @click="navigate('minha-caixa')">
          <v-list-item-title>Pontos de Descarte</v-list-item-title>
        </v-list-item>
        <v-list-item @click="navigate('itens-point')">
          <v-list-item-title>Itens Points</v-list-item-title>
        </v-list-item>
        <v-list-item @click="navigate('ranking')">
          <v-list-item-title>Ranking</v-list-item-title>
        </v-list-item>
        <v-list-item @click="navigate('metrics')">
          <v-list-item-title>Métricas</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <!-- Conteúdo Principal -->
    <v-main>
      <div class="container">
        <GoogleMap v-if="currentSection === 'minha-caixa'" />
        <ItensPoint v-if="currentSection === 'itens-point'" />
        <UserRanking v-if="currentSection === 'ranking'" />
        <UserMetrics v-if="currentSection === 'metrics'" />
      </div>
    </v-main>
  </v-app>
</template>

<script>
import GoogleMap from './components/GoogleMap.vue';
import ItensPoint from './components/ItensPoint.vue'; // Importando o novo componente
import UserRanking from './components/UserRanking.vue';
import UserMetrics from './components/UserMetrics.vue';

export default {
  name: 'App',
  components: {
    GoogleMap,
    ItensPoint, // Adicionando componente de Itens Points
    UserRanking,
    UserMetrics,
  },
  data() {
    return {
      drawer: false,
      currentSection: 'minha-caixa',
    };
  },
  methods: {
    navigate(section) {
      this.drawer = false; // Fecha o drawer
      this.currentSection = section; // Define a seção atual
    },
  },
};
</script>
