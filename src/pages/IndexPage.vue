<template>
  <q-page-container>
    <div class="searchContainer">
      <q-input
        outlined
        bottom-slots
        type="text"
        v-model="searchCli"
        label="Buscar Clientes"
        placeholder="Informe o CPF"
        mask="###.###.###-##"
      >
        <template v-slot:prepend>
          <q-icon name="search" />
        </template>
      </q-input>
      <footer class="footerSearch">
        <q-btn label="Buscar" color="primary" v-on:click="searchClient" />
      </footer>
    </div>
  </q-page-container>
  <client-card :client="clientResult" v-if="showCard" />
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { useRouter } from 'vue-router';
import ClientCard from '../components/ClientCard.vue';
export default defineComponent({
  components: { ClientCard },
  name: 'PageIndex',

  setup() {
    const router = useRouter();
    return { router };
  },
  data() {
    searchCli: String;
    clientResult: [];
    showCard: false;
  },

  methods: {
    async searchClient(searchCli) {
      this.searchCli = this.searchCli.replace(/[^0-9]/g, '');

      this.$axios
        .get(
          'http://servidorprincipal.no-ip.info:5442/api/Paciente/cpf/' +
            this.searchCli
        )
        .then((res) => {
          this.clientResult = res.data;
        })
        .catch((err) => {
          console.log(err);
        });
      this.showCard = true;
    },
  },
});
</script>

<style scoped>
.searchContainer {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  padding: 15px;
}
.footerSearch {
  display: flex;
  padding: 0 15px 0;

  align-items: center;
  align-content: center;
}
</style>
