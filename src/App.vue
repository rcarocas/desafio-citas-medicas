<template>
  <div id="app" class="container">
    <h1 class="text-center pt-3">Reserva de citas médicas</h1>
    <form action="" class="text-center container py-3 border rounded" @submit.prevent="agregarCita">
      <div class="d-md-flex flex-wrap justify-content-around p-2">
        <div>
          <label class="form-label" for="" :class="!cita.paciente ? 'text-danger' : ''">Paciente</label>
          <input class="form-control" v-model="cita.paciente" type="text" />
        </div>
        <div>
          <label class="form-label" for="" :class="!cita.fecha ? 'text-danger' : ''">Fecha</label>
          <input class="form-control" v-model="cita.fecha" type="date" />
        </div>
        <div>
          <label class="form-label" for="" :class="!cita.hora ? 'text-danger' : ''">Hora</label>
          <input class="form-control" v-model="cita.hora" type="time" />
        </div>
        <div>
          <label class="form-label" for="" :class="!cita.gravedad ? 'text-danger' : ''">Gravedad</label>
          <select name="" id="" class="form-select" v-model="cita.gravedad">
            <option :value="gravedad" v-for="(gravedad, index) in gravedades" :key="index">{{ gravedad }}</option>
          </select>
        </div>
        <div>
          <label class="form-label" for="" :class="!cita.motivo ? 'text-danger' : ''">Motivo</label>
          <input class="form-control" v-model="cita.motivo" type="text" />
        </div>
      </div>
      <div>
        <button class="btn btn-outline-secondary my-2" type="submit"
          :disabled="!cita.paciente || !cita.fecha || !cita.hora || !cita.gravedad || !cita.motivo">Agregar</button>
      </div>
    </form>
    <div>
      <p class="text-center text-danger" v-if="citas.length < 1">Aún no hay consultas registradas</p>
    </div>
    <div class="row">
      <div class="col-12 col-md-6 col-lg-4 py-3 mx-auto" v-for="(cita, index) in citas" :key="index">
              <CardCita :cita="cita" @eliminarCita="eliminarCitaHandler(index)"/>
      </div>
    </div>
  </div>
</template>

<script>
import CardCita from './components/CardCita.vue'
export default {
  name: 'App',
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
        motivo: ""
      },
      gravedades: [
        "Baja",
        "Media",
        "Alta"
      ]
    }
  },
  methods: {
    agregarCita() {
      this.citas.push(this.cita);
      this.cita = {};
    },
    eliminarCitaHandler(index){
      if(confirm("¿Estás seguro que deseas eliminar esta cita?")){
      this.citas.splice(index,1)}
    }
  }
}
</script>

<style></style>
