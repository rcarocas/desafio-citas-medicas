<template>
    <div id="cardCita">
        <div class="card text-center" style="width: 18rem;"  :class="cita.gravedad == 'Baja'? 'text-bg-success' : cita.gravedad == 'Media'? 'bg-warning' : 'text-bg-danger'" >
            <div class="card-body">
                <h6 class="card-title fw-bold mb-2 text-body-secondary">Paciente</h6>
                <p class="card-text">{{ cita.paciente }}</p>
                <h6 class="card-title fw-bold mb-2 text-body-secondary">Fecha</h6>
                <p class="card-text">{{ cita.fecha }}</p>
                <h6 class="card-title fw-bold mb-2 text-body-secondary">Hora</h6>
                <p class="card-text">{{ cita.hora }}</p>
                <h6 class="card-title fw-bold mb-2 text-body-secondary">Motivo</h6>
                <p class="card-text">{{ cita.motivo }}</p>
                <button class="btn btn-light my-2" @click="$emit('eliminarCita')">Eliminar</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "CardCita",
    props: {
        cita: Object,
    },
    data(){
        return{}
    }
}
</script>

<style scoped></style>