<template>
  <div class="form form--2">
    <form class="form form__grid">
      <FormCheckbox label="Possui algum animal de estimação?" :options="havePet" :onChange="setHavePet" />
      <FormCheckbox label="qual espécie está buscando para adotar?" :options="species" :onChange="setSpecie" />
      <FormCheckbox label="Qual porte para adotar?" :options="sizes" :onChange="setSize" />
    </form>
  </div>
</template>

<script>
import Dialogo from "@/components/Dialogo.vue";
import FormInput from '@/components/form/FormInput.vue';
import FormCheckbox from '@/components/form/FormCheckbox.vue';
export default {
  data() {
    return {
      user: {},
      havePet: [
        "Gato",
        "Cachorro",
        "Não possuo"
      ],
      species: [
        "Gato",
        "Cachorro",
      ],
      sizes: [
        'Pequeno',
        'Médio',
        'Grande'
      ]
    }
  },
  props: [
    "setUserData"
  ],
  components: {
    Dialogo,
    FormInput,
    FormCheckbox,
  },
  methods: {
    setState(item, value) {
      console.log(`change ${item} with value`, value);
      this.user[item] = value;
      this.$emit('setUserData', this.user);
    },
    setHavePet(option) {
      this.user.havePet = option;
      this.$emit('setUserData', this.user);
    },
    setSpecie(option) {
      this.user.petSpecie = option;
      this.$emit('setUserData', this.user);
    },
    setSize(option) {
      this.user.petSize = option;
      this.$emit('setUserData', this.user);
    }
  }
};
</script>

<style>

.form {
  padding: 0 20px;
}

.form__grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 20px;
}

.btn {
  font-size: 16px;
}

</style>