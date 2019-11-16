<template>
  <div class="form__group">
    <label :for="id" class="form__label">
      {{label}}
    </label>
    <input :type="type || 'text'" class="form__input" v-on:input="onChange" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      value: ''
    }
  },
  props: [
    "id",
    "label",
    "type",
    "onChange",
    "onClick",
  ],
  methods: {
  }
}
</script>

<style>

.form__group {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.form__label {
  color: #fff;
  font-size: 25px;
  margin-left: 10px;
  text-align: left;
}

.form__input {
  background-color: #fff;
  padding: 10px 20px;
  border-radius: 20px;
  border: none;
  outline: none;
}

</style>