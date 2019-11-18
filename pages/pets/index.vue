<template>
  <div class="about">
    <Header />
    <main v-if="loading || message" class="main main--loading">
      <p>{{ message ? message : "Carregando..." }}</p>
    </main>
    <main v-else-if="pets.length > 0" class="main">
      <Titulo texto="Encontrados" />
      <div class="pets">
        <div v-for="(pet, index) in pets" :key="index" class="pet">
          <div
            class="pet__image"
            :style="{
              backgroundImage: `url(&quot;${pet.image}&quot;)`
            }"
          ></div>
          <p class="pet__name">{{ pet.name }}</p>
          <p class="pet__description">{{ pet.description }}</p>
        </div>
      </div>
    </main>
    <main v-else-if="pets.length > 0" class="main">
      <p>{{ "Nenhum pet encontrado..." }}</p>
    </main>
  </div>
</template>

<script>
import Header from "@/components/common/Header.vue";
import Titulo from "@/components/Titulo.vue";
import Info from "@/components/Info.vue";
import axios from "axios";
export default {
  components: {
    Header,
    Titulo,
    Info
  },
  mounted() {
    console.log("get pets");
    this.getPets();
  },
  data() {
    return {
      loading: true,
      message: null,
      pets: null
    };
  },
  methods: {
    async getPets() {
      let res = await axios.get("http://localhost:8080/api/pet");
      console.log("pets got", res.data);
      if (res.data.length === 0)
        return (this.message = "Nenhum pet encontrado");
      this.pets = res.data;
      this.loading = false;
    }
  }
};
</script>

<style>
.main {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: var(--color-background);
  min-height: 100vh;
  padding-top: 40px;
}

.main--loading {
  align-items: center;
  justify-content: center;
  font-size: 50px;
}

.pets {
  max-width: 1190px;
  padding: 20px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  grid-gap: 20px;
}

.pet {
  background-color: var(--color-primary);
  padding: 20px;
  border-radius: 20px;
  display: flex;
  flex-direction: column;
  align-items: stretch;
}

.pet__image {
  height: 100px;
  background-size: cover;
  background-position: center;
  border-radius: 20px;
}

.pet__name {
  color: #fff;
  font-weight: bold;
  font-size: 20px;
  margin: 10px;
}

.pet__description {
  color: #fff;
  font-weight: bold;
  margin: 0 10px;
}

</style>
