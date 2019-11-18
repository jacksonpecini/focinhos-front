 <template>
  <div class="adotar">
    <Header />
    <main class="main">
      <Titulo texto="Mais Sobre Você" />
      <Info>
        <div class="adotar__content">
          <div class="adotar__body">
            <Form1 v-if="activeIndex === 0" />
            <Form2 @setUserData="setUserData" v-if="activeIndex === 1" />
            <Form3 @setUserData="setUserData" v-if="activeIndex === 2" />
            <Form4 @setUserData="setUserData" v-if="activeIndex === 3" />
            <Form5 @setUserData="setUserData" v-if="activeIndex === 4" />
          </div>
          <div class="adotar__footer">
            <div class="footer__options">
              <div
                v-for="(item, index) in slides"
                :key="index"
                :class="[`option`, index === activeIndex ? 'option--active' : '']"
                v-on:click="() => goToSlide(index)"
              ></div>
            </div>
            <div class="footer__actions">
              <Button v-if="activeIndex < 4" texto="Continuar" type="button" :onClick="() => { activeIndex +=1 }" />
              <Button v-else texto="Finalizar" type="button" :onClick="submit" />
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
import Button from '@/components/Button.vue';
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
      user: {},
    };
  },
  methods: {
    goToSlide(index) {
      console.log("go to index", index);
      this.activeIndex = index;
    },
    setUserData(data) {
      console.log('set user data', data);
      this.user = {
        ...this.user,
        ...data
      }
      console.log('current user', this.user);
    },
    async submit() {
      console.log('submit data', this.user);
      let res = await axios.post('http://localhost:8080/api/user', this.user);
      localStorage.email = res.data.email;
      window.location.pathname = '/pets';
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

.adotar {
}

.adotar__content {
  position: relative;
  height: 500px;
  color: #000;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
}

.adotar__image {
  position: absolute;
  top: 270px;
  left: 583px;
  width: 120px;
  height: 120px;
  transform: rotate(90deg);
}

.dialogo {
  margin-top: 40px;
}

.adotar__body {
  padding-top: 40px;
  min-height: 240px;
}

.adotar__footer {
  display: flex;
  flex-direction: column;
  margin-top: 40px;
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
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

.btn {
  font-size: 16px;
}

</style>


