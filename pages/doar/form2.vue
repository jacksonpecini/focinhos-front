<template>
  <div class="form form--2">
    <form class="form form__grid">
      <FormInput id="state" label="Nome" :onChange="(e) => setState('name', e.target.value)" />
      <FormInput id="state" label="Descrição" :onChange="(e) => setState('description', e.target.value)" />
      <FormCheckbox label="Qual é a espécie" :options="specieOptions" :onChange="setSpecie" />
      <FormCheckbox label="Gênero do animal" :options="['Feminino', 'Masculino']" :onChange="setGender" />
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
      pet: {},
      specieOptions: [
        "Gato",
        "Cachorro"
      ],
    }
  },
  props: [
    "setPetData"
  ],
  components: {
    Dialogo,
    FormInput,
    FormCheckbox,
  },
  methods: {
    setState(item, value) {
      console.log(`change ${item} with value`, value);
      this.pet[item] = value;
      let data = {...this.pet};
      console.log('data to set', data);
      this.$emit('setPetData', data);
    },
    setSpecie(specie) {
      this.pet.specie = specie;
      this.$emit('setPetData', this.pet);
    },
    setGender(gender) {
      this.pet.gender = gender;
      this.$emit('setPetData', this.pet);
    },
  }
};
</script>

<style>

.form {

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