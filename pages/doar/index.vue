<template>
  <div class="doar">
    <Header />
    <main class="main">
      <Titulo texto="Doação" />
      <Info>
        <div v-if="loading || message" class="doar__content doar__content--loading">
          <p>{{message ? message : 'Carregando...'}}</p>
        </div>
        <div v-else class="doar__content">
          <div class="doar__body">
            <Form1 v-if="activeIndex === 0" />
            <Form2 v-if="activeIndex === 1" @setPetData="setPetData" />
            <Form3 v-if="activeIndex === 2" @setPetData="setPetData" />
            <Form4 v-if="activeIndex === 3" @setPetData="setPetData" />
            <Form5 v-if="activeIndex === 4" :setFile="setFile" />
          </div>
          <div class="doar__footer">
            <div class="footer__options">
              <div
                v-for="(item, index) in slides"
                :key="index"
                :class="[
                  `option`,
                  index === activeIndex ? 'option--active' : ''
                ]"
                v-on:click="() => goToSlide(index)"
              ></div>
            </div>
            <div class="footer__actions">
              <Button
                v-if="activeIndex < 4"
                texto="Continuar"
                type="button"
                :onClick="
                  () => {
                    activeIndex += 1;
                  }
                "
              />
              <Button
                v-else
                texto="Finalizar"
                type="button"
                :onClick="submit"
              />
            </div>
          </div>
        </div>
      </Info>
    </main>
  </div>
</template>

<script>
import Header from "@/components/common/Header.vue";
import Titulo from "@/components/Titulo.vue";
import Info from "@/components/Info.vue";
import Dialogo from "@/components/Dialogo.vue";
import Form1 from "./form1.vue";
import Form2 from "./form2.vue";
import Form3 from "./form3.vue";
import Form4 from "./form4.vue";
import Form5 from "./form5.vue";
import Button from "@/components/Button.vue";
import axios from 'axios';
export default {
  components: {
    Header,
    Titulo,
    Info,
    Dialogo,
    Form1,
    Form2,
    Form3,
    Form4,
    Form5,
    Button
  },
  data() {
    return {
      activeIndex: 0,
      loading: false,
      message: null,
      pet: {},
      slides: [
        {
          id: 0
        },
        {
          id: 1
        },
        {
          id: 2
        },
        {
          id: 3
        },
        {
          id: 4
        }
      ],
      formData: null
    };
  },
  methods: {
    goToSlide(index) {
      console.log("go to index", index);
      this.activeIndex = index;
    },
    setPetData(data) {
      console.log("set pet data", data);
      this.pet = {
        ...this.pet,
        ...data
      };
      console.log("current pet", this.pet);
    },
    setFile(e) {
      console.log('set file', e.target.files[0]);
      this.formData = new FormData();
      this.formData.append('image', e.target.files[0]);
    },
    async submit() {
      this.loading = true;
      for (let item of Object.keys(this.pet)) {
        this.formData.append(item, this.pet[item]);
      }
      let res = await axios.post("http://localhost:8080/api/pet", this.formData, {
        headers: {
          "Content-Type": "multipart/form-data"
        }
      });
      console.log('sent files', res.data);
      this.message = 'Pet cadastrado com sucesso!'
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
}

.titulo {
  margin: 40px 0;
}

.doar {
}

.doar__content {
  position: relative;
  height: 400px;
  color: #000;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
}

.doar__content--loading {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 30px;
  color: #fff;
}

.doar__image {
  position: absolute;
  top: 20px;
  left: -10px;
  width: 120px;
  height: 100px;
  transform: rotate(90deg);
}

.dialogo {
  margin-top: 40px;
}
.dialogo::after {
  margin-top: 40px;
  top: -40px;
  transform: rotate(45deg);
  left: -10px;
}

.doar__body {
  padding-top: 40px;
  padding-left: 40px;
  padding-right: 40px;
  min-height: 250px;
}

.doar__footer {
  display: flex;
  flex-direction: column;
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
}

.btn {
  font-size: 16px;
  margin-bottom: 10px;
}

.footer__options {
  display: flex;
  padding: 20px;
  position: relative;
  border-top: 1px solid #fff;
}

.option {
  width: 20px;
  height: 20px;
  background-color: var(--color-grey);
  border-radius: 100%;
  margin: 0 5px;
  cursor: pointer;
}

.option--active {
  background-color: white;
}
</style>
