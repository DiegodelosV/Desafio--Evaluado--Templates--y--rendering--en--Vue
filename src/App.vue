<script>
export default {
  name: "App",
  data() {
    return {
      colorDeFondo: "darkgreen",
      colorDeTexto: "white",
      mostrarTexto: false,
      RadioBorde: 0,
      tipografia: "cursive",
      opaco: false,
      contenidoTextual: "",
      tamanoDeLetra: ["Pequeño", "Mediano", "Grande"],
      tamanoDeLetraSeleccionado: "Pequeño",
    };
  },
};
</script>
<template>
  <main>
    <!-- Formulario -->
    <form class="form">
      <!-- Input color de fondo -->
      <div>
        <label for="colorDeFondo">Color de fondo</label>
        <input
          v-model="colorDeFondo"
          type="text"
          id="colorDeFondo"
          placeholder="darkgreen"
        />
      </div>

      <!-- Input color de texto -->
      <div>
        <label for="colorDeTexto">Color de texto</label>
        <input
          v-model="colorDeTexto"
          type="text"
          id="colorDeTexto"
          placeholder="white"
        />
      </div>

      <!--  Input checkbox para mostrar texto -->
      <div>
        <label for="mostrarTexto">Mostrar texto</label>
        <input type="checkbox" id="mostrarTexto" v-model="mostrarTexto" />
      </div>

      <!-- Input range para modificar radio borde -->
      <div>
        <label for="RadioBorde">Borde</label>
        <input
          v-model="RadioBorde"
          type="range"
          id="RadioBorde"
          min="0"
          max="100"
        />
      </div>

      <!-- textarea para Contenido textual -->
      <div>
        <label for="contenidoTextual">Contenido textual</label>
        <textarea
          v-model="contenidoTextual"
          id="contenidoTextual"
          rows="4"
        ></textarea>
      </div>

      <!-- Select para Tipografía -->
      <div>
        <div><label for="tipografia">Tipografía</label></div>
        <select v-model="tipografia" id="tipografia">
          <option value="cursive">Cursive</option>
          <option value="serif">Serif</option>
          <option value="sans-serif">Sans-serif</option>
          <option value="fantasy">Fantasy</option>
          <option value="monospace">Monospace</option>
        </select>
      </div>

      <!-- Input checkbox para Opaco -->
      <div>
        <label for="opaco">Opaco</label>
        <input type="checkbox" id="opaco" v-model="opaco" />
      </div>

      <!--  input radio para tamaño de letra -->
      <div>
        <label>Tamaño de letra</label>
        <div class="radioInput">
          <div
            class="radioItems"
            v-for="fontSize in tamanoDeLetra"
            :key="fontSize"
          >
            <input
              type="radio"
              name="tamanoDeLetra"
              :value="fontSize"
              v-model="tamanoDeLetraSeleccionado"
            />
            <label>{{ fontSize }}</label>
          </div>
        </div>
      </div>
    </form>

    <!-- Contenedor muestra datos ingresados en el Formulario, que modificaran el CSS  -->
    <div
      class="container"
      :style="{
        backgroundColor: colorDeFondo,
        color: colorDeTexto,
        borderRadius: RadioBorde + '%',
        opacity: opaco ? 0 : 1,
        fontFamily: tipografia,
      }"
      :class="{
        'text-small': tamanoDeLetraSeleccionado === 'Pequeño',
        'text-medium': tamanoDeLetraSeleccionado === 'Mediano',
        'text-large': tamanoDeLetraSeleccionado === 'Grande',
      }"
    >
      <p v-show="mostrarTexto">{{ contenidoTextual }}</p>
    </div>
  </main>
</template>

<style scoped>
main {
  display: flex;
  align-items: flex-start;
  gap: 20px;
}

.form {
  display: flex;
  flex-direction: column;
  border: 1px solid black;
  color: white;
  padding: 1rem;
  width: 400px;
  background-color: #2a2a2e;
  box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.2);
  margin-right: 3rem;
}

.container {
  display: flex;
  flex-direction: column;
  padding: 1rem;
  text-align: center;
  justify-content: center;
  margin-top: 3rem;
  width: 300px;
  height: 300px;
}

.text-small {
  font-size: 1rem;
}

.text-medium {
  font-size: 2rem;
}

.text-large {
  font-size: 4rem;
}

input[type="text"],
input[type="range"],
textarea {
  width: 100%;
  margin-bottom: 0.5rem;
}

textarea {
  resize: vertical;
}

.radioInput {
  display: flex;
  align-items: center;
}

.radioItems {
  margin-right: 1rem;
}

div {
  margin-bottom: 0.5rem;
}
</style>
