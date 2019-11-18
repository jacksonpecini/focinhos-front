<template>
  <div class="form form--2">
    <form class="form form__grid">
      <FormCheckbox label="Você é estudante?" :options="studentOptions" :onChange="setStudent" />
      <FormInput id="state" label="Quantas pessoas moram com você?" :onChange="(e) => setState('qtdPeople', e.target.value)" />
      <FormCheckbox label="Quem são as pessoas que moram com você?" :options="peopleOptions" :onChange="setPeopleType" />
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
      studentOptions: [
        "Sim",
        "Não"
      ],
      peopleOptions: [
        "Familiares",
        "Amigos",
        "Cônjuge"
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
    setStudent(option) {
      if(option === 'Sim') {
        this.user.isStudent = true;
      } else {
        this.user.isStudent = false;
      }
      this.$emit('setUserData', this.user);
    },
    setPeopleType(option) {
      this.user.peopleType = option;
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