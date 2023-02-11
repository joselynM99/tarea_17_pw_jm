<template>
  <div>
    <h1>Consultar un estudiante</h1>
    <input v-model="id" placeholder="ID de estudiante" />
    <button v-on:click="consultarEstudiante(id)">Consultar</button>
  </div>

  <div>
    <label for="">Nombre:</label>
    <input v-model="nombre">
    <label for="">Apellido:</label>
    <input v-model="apellido">
    <label for="">Fecha de Nacimiento:</label>
    <input v-model="fechaNacimiento">
    <label for="">Salario:</label>
    <input v-model="salario">
  </div>

</template>

<script>
export default {
  data() {
    return {
      id: null,
      nombre: null,
      apellido: null,
      fechaNacimiento: null,
      salario: null
    }
  },
  methods: {
    async consultarEstudiante(id) {
      console.log("http://localhost:8081/API/Matricula/V1/estudiantes/"
        + id)
      const { nombre, apellido, fechaNacimiento, salario } = await fetch(
        "http://localhost:8081/API/Matricula/V1/estudiantes/"
        + id
      ).then((result) => result.json());

      this.nombre = nombre
      this.apellido = apellido
      this.fechaNacimiento = fechaNacimiento
      this.salario = salario

    },


  }

}
</script>

<style>
div {
  display: grid;
  width: 500px;
  margin: 10px auto;
}

button {
  width: 100px;
  text-align: center;
  margin: 10px auto;
}
</style>