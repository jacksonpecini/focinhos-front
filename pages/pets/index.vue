<template>
  <div class="about">
    <Header />
    <main v-if="loading || message" class="main main--loading">
      <p>{{ message ? message : "Carregando..." }}</p>
    </main>
    <main v-else-if="pets.length > 0" class="main">
      <Titulo texto="Encontrados" />
      <div class="pets">
        <div
          v-for="(pet, index) in pets"
          :key="index"
          class="pet"
          v-on:click="() => openModal(pet)"
        >
          <div
            class="pet__image"
            :style="{
              backgroundImage: `url(&quot;${pet.image}&quot;)`
            }"
          ></div>
          <p class="pet__name">{{ pet.name }}</p>
        </div>
      </div>
    </main>
    <main v-else-if="pets.length > 0" class="main">
      <p>{{ "Nenhum pet encontrado..." }}</p>
    </main>
    <div v-if="showModal && pet" class="modal">
      <div class="modal__shadow" v-on:click="showModal = false"></div>
      <div class="modal__card">
        <div
          class="modal__image"
          :style="{
            backgroundImage: `url(&quot;${pet.image}&quot;)`
          }"
        ></div>
        <div class="modal__name">
          {{ pet.name }}
        </div>
        <div class="modal__actions">
          <Button texto="Adotar" type="button" :onClick="adopt" />
        </div>
        <div class="modal__description">
          <p>
            {{ pet.description }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "@/components/common/Header.vue";
import Titulo from "@/components/Titulo.vue";
import Info from "@/components/Info.vue";
import Button from "@/components/Button.vue";
import axios from "axios";
export default {
  components: {
    Header,
    Titulo,
    Info,
    Button
  },
  mounted() {
    console.log("get pets");
    this.getPets();
  },
  data() {
    return {
      loading: true,
      message: null,
      pets: null,
      showModal: false,
      pet: null
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
    },
    openModal(pet) {
      console.log("open modal", pet);
      this.pet = pet;
      this.showModal = true;
    },
    adopt() {
      console.log("adotar");
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

.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal__shadow {
  background-color: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal__card {
  background-color: var(--color-primary);
  width: 500px;
  height: 400px;
  border-radius: 25px;
  padding: 20px;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 20px;
  z-index: 10;
  color: #fff;
  font-size: 18px;
}

.modal__image {
  width: 150px;
  height: 150px;
  background-size: cover;
  background-position: center;
  border-radius: 100%;
}

.modal__name {
  grid-column: 1 / 2;
  grid-row: 2 / 3;
}

.modal__description {
  grid-column: 2 / 3;
}

.modal__actions {
  grid-row: 3 / 4;
}

.btn {
  font-size: 16px;
}

</style>
