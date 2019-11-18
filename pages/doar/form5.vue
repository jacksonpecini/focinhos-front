<template>
  <div class="form form--2">
    <form class="form form__grid">
      <input type="file" class="form__input form__file" v-on:input="setFile">
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
    }
  },
  props: [
    "setFile"
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