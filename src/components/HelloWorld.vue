<template>
  <div id="desafioComponent">
      <section>
          <form>
              <div id="backgroundField">
                  <label>Color de fondo</label>
                  <!-- 01 Le dimos un nombre a la variable -->
                  <input type="text" v-model="backgroundField">
              </div>
              <div>
                  <label>Color de texto</label>
                  <!-- 04 Le dimos un nombre a la variable de estado para el input de cambio de color del texto -->
                  <input type="text" v-model="colorTexto">
              </div>
              <div id="checkField">
                  <label>Mostrar texto</label>
                  <!-- 07 Le dimos un nombre a la variable -->
                  <input type="checkbox" class="width-auto" v-model="mostrarTexto">
              </div>
              <div>
                  <label>Borde</label>
                  <!-- 10 Establecimos el minimo y maximo de rango y asignamos el nombre de la variable -->
                  <input type="range" min="10" max="100" v-model="radioBorde">
              </div>
              <div>
                  <label>Contenido textual</label>
                  <!-- 13 Asignamos el nombre a la variable de estado -->
                  <textarea v-model="contenidoTextual"></textarea>
              </div>
              <div>
                  <label>Tipografía</label>
                  <!-- 14 Asignamos el nombre a la variable de estado del select -->
                  <select v-model="tipoTipografia">
                      <!-- 15 Asignamos las variables de tipo de tipografia usando v-for -->
                      <option :value="tipografia" v-for="tipografia in tipografias" :key="tipografia">{{ tipografia }}</option>
                  </select>
              </div>
              <div>
                  <label>Opaco</label>
                  <input type="checkbox" class="width-auto">
              </div>
              <div>
                  <p>Tamaño de letra</p>
                  <div id="textSize">
                      <label>Pequeño</label>
                      <input type="radio" value="Pequeño">
                      <label>Mediano</label>
                      <input type="radio" value="Mediano">
                      <label>Grande</label>
                      <input type="radio" value="Grande">
                  </div>
              </div>
          </form>
      </section>
      <section id="content">
          
          <div id="textBox" :style="{background: backgroundField, borderRadius: radioBorde + 'px'}">
              
              <p id="mainText" :style="{color: colorTexto, fontFamily: tipoTipografia}" v-show="mostrarTexto">{{ contenidoTextual }}</p>
          </div>
      </section>
  </div>
</template>

<script>
  export default {
      name: 'App',
      data() {
          return {
              backgroundField:'blue', //02 Capturamos el valor del input
              colorTexto: 'white', //05 Capturamos el valor del input
              mostrarTexto: false, //08 capturamos el estado del checkbox y definimos como valor por defecto false
              contenidoTextual: 'Este es un texto generado por Vue', // 09 Establecimos el texto que aparecerá dentro del contenedor
              radioBorde: '50', // 11 Capturamos el valor del range y establecimos un valor por defecto
              tipoTipografia: 'cursive', // 16 Capturamos el valor del select y asignamos el valor por defecto a la variable tipoTipografia
              tipografias: ["fantasy", "cursive", "monospace"], // 17 Agregamos como valor para los input, el arreglo con los tipos de tipografia
              
          }
      }
  }
</script>

<style>
  #desafioComponent {
      display: grid;
      grid-template-columns: auto auto;
      width: 100%;
  }

  form {
      background: #004d40;
      color: #fff;
      width: 70%;
      margin: 0 auto;
  }

  form div {
      margin: 20px;
  }

  form div label {
      float: left;
  }

  form div input, form div textarea, select {
      width: 100%;
  }

  #backgroundField {
      padding-top: 20px;
  }

  p {
      text-align: left;
  }

  .width-auto {
      width: auto;
  }

  #textSize {
      display: flex;
      padding-bottom: 20px;
  }

  #content {
      width: 100%;
      display: flex;
      align-items: center;
  }

  #textBox {
      width: 350px;
      height: 350px;
      margin: 0 auto;
      display: flex;
      justify-content: center;
      align-items: center;
  }

  #mainText {
      color: #000;
  }
</style>