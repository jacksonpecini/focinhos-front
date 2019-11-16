<template>
  <div class="form form--2">
    <form class="form form__grid">
      <FormInput id="state" label="Estado onde mora" :onChange="(e) => setState('state', e.target.value)" />
      <FormInput id="state" label="Cidade" :onChange="(e) => setState('city', e.target.value)" />
      <FormInput id="state" label="Bairro" :onChange="(e) => setState('neighborhood', e.target.value)" />
      <FormInput id="state" label="Tipo de moradia" :onChange="(e) => setState('type', e.target.value)" />
    </form>
  </div>
</template>

<script>
import Dialogo from "@/components/Dialogo.vue";
import FormInput from '@/components/form/FormInput.vue';
export default {
  data() {
    return {
      user: {}
    }
  },
  props: [
    "setUserData"
  ],
  components: {
    Dialogo,
    FormInput,
  },
  methods: {
    setState(item, value) {
      console.log(`change ${item} with value`, value);
      this.user[item] = value;
      let data = {...this.user};
      console.log('data to set', data);
      this.$emit('setUserData', data);
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