<template>
  <div class="form form--2">
    <form class="form form__grid">
      <FormCheckbox label="Idade?" :options="age" :onChange="setAge" />
      <FormCheckbox label="Qual é a espécie?" :options="species" :onChange="setSpecie" />
      <FormCheckbox label="Gênero do animal" :options="genders" :onChange="setGender" />
      <FormCheckbox label="Tem alguma necessidade especial?" :options="special" :onChange="setSpecial" />
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
      age: [
        "Filhote",
        "Adulto",
        "Idoso"
      ],
      species: [
        "Gato",
        "Cachorro",
      ],
      genders: [
        "Feminino",
        "Masculino",
      ],
      special: [
        'Sim',
        'Não',
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
    setAge(option) {
      this.user.age = option;
      this.$emit('setUserData', this.user);
    },
    setSpecie(option) {
      this.user.petSpecie = option;
      this.$emit('setUserData', this.user);
    },
    setGender(option) {
      this.user.petGender = option;
      this.$emit('setUserData', this.user);
    },
    setSpecial(option) {
      this.user.petSpecial = option;
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