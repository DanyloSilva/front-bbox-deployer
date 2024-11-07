<template>
  <v-container>
    <v-card outlined class="pa-4">
      <v-card-title>Métricas do Usuário</v-card-title>
      <v-card-text>
        <!-- Métrica de Lixo Eletrônico -->
        <div class="metric">
          <h3>Lixo Eletrônico Descartado</h3>
          <v-progress-linear :value="wastePercentage" color="green" height="20"></v-progress-linear>
          <v-chip color="green" dark>{{ wasteDiscarded }} kg</v-chip>
        </div>

        <!-- Métrica de Recifecoins -->
        <div class="metric mt-4">
          <h3>Recifecoins Acumulados</h3>
          <v-progress-linear :value="coinPercentage" color="blue" height="20"></v-progress-linear>
          <v-chip color="blue" dark>{{ recifecoins }} Recifecoins</v-chip>
        </div>

        <!-- Outras métricas de exemplo -->
        <div class="metric mt-4">
          <h3>Número de Descartes</h3>
          <v-chip color="indigo" dark>{{ disposalsCount }} Descartes</v-chip>
        </div>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: 'UserMetrics',
  data() {
    return {
      // Mock de dados para exibição
      wasteDiscarded: 12, // em kg
      recifecoins: 150, // moedas acumuladas
      disposalsCount: 5, // vezes que o usuário descartou
    };
  },
  computed: {
    // Valores calculados para o preenchimento das barras
    wastePercentage() {
      return (this.wasteDiscarded / 50) * 100; // Baseado em um máximo de 50 kg
    },
    coinPercentage() {
      return (this.recifecoins / 200) * 100; // Baseado em um máximo de 200 Recifecoins
    },
  },
};
</script>

<style scoped>
.metric {
  display: flex;
  flex-direction: column;
  gap: 8px;
}
</style>
