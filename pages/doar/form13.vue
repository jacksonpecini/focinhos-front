<template>
  <div class="form form--2">
    <form class="form form__grid">
      <FormCheckbox label="Pelagem" :options="pelagem" :onChange="setPelagem" />
      <FormCheckbox label="Possue raça?" :options="race" :onChange="setRace" />
      <FormCheckbox label="É castrado?" :options="castrado" :onChange="setCastrado" />
      <FormCheckbox label="Qual seu porte?" :options="sizes" :onChange="setSize" />
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
      pelagem: [
        "Curta",
        "Média",
        "Longa"
      ],
      race: [
        "Sim",
        "Não",
      ],
      castrado: [
        "Sim",
        "Não",
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
    setPelagem(option) {
      this.user.pelagem = option;
      this.$emit('setUserData', this.user);
    },
    setRace(option) {
      this.user.petRace = option;
      this.$emit('setUserData', this.user);
    },
    setCastrado(option) {
      this.user.petGender = option;
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