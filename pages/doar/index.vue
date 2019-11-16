 <template>
  <div class="doar">
    <Header />
    <main class="main">
      <Titulo texto="Doação" />
      <Info>
        <div class="doar__content">
          <img src="~/assets/dog.png" class="doar__image" alt />
          <div class="doar__body">
            <Form10 v-if="activeIndex === 0" />
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
export default {
  components: {
    Header,
    Titulo,
    Info,
    Dialogo,
    Form10,
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
  min-height: 250px;
  
}

.doar__footer{
  display: flex;
  position: relative;
  bottom: -95px;
}

.footer__options {
  display: flex;
  padding: 20px;
  position: relative;
  border-top: solid;
  border-top-color: white;
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

