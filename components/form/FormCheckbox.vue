<template>
  <div class="form__group">
    <label class="form__label">
      {{label}}
    </label>
    <div class="form__options">
      <div v-for="(item, index) in options" :key="index" class="form__option">
        <div :class="['option__icon', activeIndex !== null && activeIndex === index ? 'option__icon--selected': '']" v-on:click="() => setOption(index)"></div>
        <div class="option__label">{{item}}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeIndex: null
    }
  },
  props: [
    "label",
    "options",
    "onChange"
  ],
  methods: {
    setOption(index) {
      this.activeIndex = index;
      return this.onChange(this.options[index]);
    }
  }
}
</script>

<style>

.form__group {

}

.form__options {
  display: flex;
  flex-direction: column;
}

.form__option {
  display: flex;
  padding: 5px;
}

.option__icon {
  width: 25px;
  height: 25px;
  background-color: var(--color-background);
  border-radius: 100%;
  cursor: pointer;
  margin-right: 10px;
}

.option__icon--selected {
  background-color: var(--color-orange);
}

</style>