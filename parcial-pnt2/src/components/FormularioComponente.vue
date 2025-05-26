<template>
  <div class="formulario">
    <form @submit.prevent>
      <div class="form-group">
        <label for="inputText">Ingrese texto:</label>
        <input
          v-model.trim="inputText"
          id="inputText"
          type="text"
          class="form-control"
          placeholder="Ingrese el texto aquí"
        />
      </div>
    </form>

    <div class="mt-3 resultados">
      <p><strong>Caracteres ingresados:</strong> {{ contadorCaracteres }}</p>
      <p><strong>Codificado:</strong> {{ cambioVocales }}</p>
      <p><strong>Todo en mayúscula:</strong> {{ mayusculas }}</p>
      <p><strong>Todo en minúscula:</strong> {{ minusculas }}</p>
      <p><strong>Intercalado (Mayúscula primero):</strong> {{ intercaladoMayuscula }}</p>
      <p><strong>Intercalado (Minúscula primero):</strong> {{ intercaladoMinuscula }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "FormularioComponente",
  data() {
    return {
      inputText: ""
    };
  },
  computed: {
    contadorCaracteres() {
      return this.inputText.length;
    },
    cambioVocales() {
      return this.inputText.toLowerCase().replace(/[aeiou]/g, function (match) {
        switch (match) {
          case 'a': return 'u';
          case 'e': return 'o';
          case 'i': return 'i';
          case 'o': return 'e';
          case 'u': return 'a';
        }
      });
    },
    mayusculas() {
      return this.inputText.toUpperCase();
    },
    minusculas() {
      return this.inputText.toLowerCase();
    },
    intercaladoMayuscula() {
      return this.intercalado(this.inputText, true);
    },
    intercaladoMinuscula() {
      return this.intercalado(this.inputText, false);
    }
  },
  methods: {
      intercalado(text, conMayuscula) {
      let result = '';
      for (let i = 0; i < text.length; i++) {
        if (conMayuscula) {
          result += i % 2 === 0 ? text[i].toUpperCase() : text[i].toLowerCase();
        } else {
          result += i % 2 === 0 ? text[i].toLowerCase() : text[i].toUpperCase();
        }
      }
      return result;
    }
  }
};
</script>

<style scoped>
.formulario {
  max-width: 600px;
  margin: 2rem auto;
}
.form-control {
  width: 100%;
  padding: 0.5rem;
}
.resultados {
  margin-top: 1rem;
  padding: 1rem;
  background-color: #f5f5f5;
  border-radius: 6px;
}
</style>