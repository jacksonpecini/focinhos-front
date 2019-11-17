 <template>
  <div class="doar">
    <Header />
    <main class="main">
      <Titulo texto="Doação" />
      <Info>
        <div class="doar__content">
          <div class="doar__body">
            <Form10 v-if="activeIndex === 0" />
            <Form11 @setUserData="setUserData" v-if="activeIndex === 1" />
            <Form12 @setUserData="setUserData" v-if="activeIndex === 2" />
            <Form13 @setUserData="setUserData" v-if="activeIndex === 3" />
          </div>
          <div class="doar__footer">
            <div class="footer__options">
              <div
                v-for="(item, index) in slides"
                :key="index"
                :class="[`option`, index === activeIndex ? 'option--active' : '']"
                v-on:click="() => goToSlide(index)"
              ></div>
            </div>
            <div class="footer__actions"></div>
             <Button v-if="activeIndex < 3" texto="Continuar" type="button" :onClick="() => { activeIndex +=1 }" />
             <Button v-else texto="Finalizar" type="button" :onClick="submit" />
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
import Form10 from "./form10.vue";
import Form11 from "./form11.vue";
import Form12 from "./form12.vue";
import Form13 from "./form13.vue";
import Button from "@/components/Button.vue";
export default {
  components: {
    Header,
    Titulo,
    Info,
    Dialogo,
    Form10,
    Form11,
    Form12,
    Form13,
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
        }
      ]
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
    submit() {
      console.log('submit data', this.user);
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
  height: 500px;
  color: #000;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
}

.doar__image {
  position: absolute;
  top: 270px;
  left: 837px;
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
  min-height: 250px;
  
}

.doar__footer{
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

