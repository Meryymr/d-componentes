<template>
  <div id="app" class="container text-center py-3">
    <main>
      <h1>Citas médicas</h1>
      <form class="border border-dark rounded py-5"
        @submit.prevent="agregarCita">
        <div class="d-md-flex flex-wrap justify-content-evenly">
          <!--PACIENTES-->
          <div>
            <label for="" class="form-label"
              :class="!cita.paciente ? 'text-danger' : ''">Paciente: </label>
            <input type="text" class="form-control" v-model="cita.paciente" />
          </div>
          <!--FECHA-->
          <div>
            <label for="" class="form-label"
              :class="!cita.fecha ? 'text-danger' : ''"> Fecha: </label>
            <input type="date" class="form-control" v-model="cita.fecha" />
          </div>
          <!--HORA-->
          <div>
            <label for="" class="form-label"
              :class="!cita.hora ? 'text-danger' : ''">Hora: </label>
            <input type="time" class="form-control" v-model="cita.hora" />
          </div>
          <!--GRAVEDAD-->
          <div>
            <label for="" class="form-label"
              :class="!cita.gravedad ? 'text-danger' : ''">Gravedad: </label>
            <select name="" id="" class="form-select" v-model="cita.gravedad">
              <option :value="gravedad" v-for="(gravedad, index) in gravedades"
                :key="index">{{ gravedad }}</option>
            </select>
          </div>
          <!--MOTIVO-->
          <div>
            <label for="" class="form-label"
              :class="!cita.motivo ? 'text-danger' : ''">Motivo: </label>
            <input type="text" class="form-control" v-model="cita.motivo" />
          </div>
        </div>
        <div class="py-3">
          <button type="submit" class="btn btn-dark my-3"
            :disabled="!cita.paciente || !cita.fecha || !cita.hora || !cita.gravedad || !cita.motivo">Agregar</button>
        </div>
      </form>
      <div>
        <p class="pt-2 text-danger" v-if="citas.length < 1">Aún no hay consultas
          registradas</p>
        <div v-else class="row">
          <div class="col-12 col-md-6 col-lg-4 py-3"
            v-for="(cita, index) in citas" :key="index">
            <CardCita :cita="cita" @eliminarCita="eliminarCitaHandler(index)" />
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import CardCita from "./components/CardCita.vue";
export default {
  name: "App",
  components: {
    CardCita
  },
  data() {
    return {
      citas: [],
      cita: {
        paciente: "",
        fecha: "",
        hora: "",
        gravedad: "",
        motivo: "",
      },
      gravedades: [
        "Baja",
        "Media",
        "Alta",
      ],
    };
  },
  methods: {
    agregarCita() {
      this.citas.push(this.cita);
      this.cita = {}
    },
    eliminarCitaHandler(index) {
      if (confirm('¿Estás seguro que deseas eliminar ésta cita?')) { this.citas.splice(index, 1) }
    }
  },
  computed: {},
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: "Inconsolata", monospace;
}
</style>
