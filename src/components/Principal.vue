<template>
  <div class="container-principal">
    <div class="container-custom">
      <div>
        <h1 class="title-custom">Calculadora de pollo por guacal</h1>
        <h3 class="subtitle-custom">Digité el número total de guacales:</h3>
        <input type="number" v-model="cratesNumber" />
        <h3 class="subtitle-custom">Digité el número total de pollos:</h3>
        <input type="number" v-model="chickenNumber" />
        <div class="error" v-if="error">
          {{ errorMessage }}
        </div>
        <h3>Resultado:</h3>
        <span>{{ resultFinal }}</span>
      </div>
      <div class="button-custom">
        <button @click="result">Hecho</button>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Principal",
  data() {
    return {
      resultFinal: "",
      chickenNumber: 0,
      cratesNumber: 0,
      error: false,
      errorMessage: "",
    };
  },
  methods: {
    result() {
      let spare = 0;
      let crates = 0;
      this.error = false;
      if (parseInt(this.chickenNumber) >= parseInt(this.cratesNumber)) {
        let numberChickenXCrates = Math.trunc(
          parseInt(this.chickenNumber) / parseInt(this.cratesNumber)
        );
        spare =
          parseInt(this.chickenNumber) -
          numberChickenXCrates * parseInt(this.cratesNumber);
        crates = this.cratesNumber - spare;
        if (parseInt(this.chickenNumber) % parseInt(this.cratesNumber) == 0) {
          this.resultFinal = `El número de guales al ${numberChickenXCrates} es ${crates};`;
        } else {
          this.resultFinal = `El número de guales al ${numberChickenXCrates} es ${crates}; El número de guacales al ${
            numberChickenXCrates + 1
          } es ${spare}`;
        }
      } else {
        this.error = true;
        this.errorMessage = `Error:El número de guacales debe ser menor a la cantidad de pollos total.`;
        this.resultFinal = "";
      }
    },
  },
};
</script>
<style scoped>
* {
  padding: 0;
  margin: 0;
}
.error {
  color: red;
}
.button-custom {
  padding-top: 20px;
}
.button-custom button {
  background: #008080;
  font-size: 25px;
  width: 200px;
}
.title-custom {
  padding: 20px 0 20px 0;
}
.subtitle-custom {
  padding: 20px 0 20px 0;
}
input {
  width: 250px;
  padding: 0 0 10px 0;
}
.container-principal {
  display: flex;
  background: #008080;
  justify-content: center;
  align-items: center;
}
.container-custom {
  margin-top: 2%;
  padding: 30px 10px;
  width: 500px;
  background-color: white;
  border: 1px solid #008080;
  border-radius: 20px;
}
@media (max-width: 300px) {
  .container-custom {
    width: 200px;
  }
  input {
    width: 100px;
    padding: 0 0 10px 0;
  }
  .button-custom button {
  background: #008080;
  font-size: 25px;
  width: 150px;
}
}
</style>
