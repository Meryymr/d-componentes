<template>
    <div id="cardPaciente">
        <div class="card"
            :style="{ backgroundColor: cita.gravedad == 'Baja' ? 'greenyellow' : cita.gravedad == 'Media' ? 'yellow' : cita.gravedad == 'Alta' ? 'red' : '' }">
            <div class="card-body">
                <h6 class="card-title fw-bolder">Paciente</h6>
                <p class="card-text"> {{ cita.paciente }}</p>
                <h6 class="card-title fw-bolder">Fecha</h6>
                <p class="card-text"> {{ cita.fecha }}</p>
                <h6 class="card-title fw-bolder">Hora</h6>
                <p class="card-text"> {{ cita.hora }}</p>
                <h6 class="card-title fw-bolder">Motivo</h6>
                <p class="card-text"> {{ cita.motivo }}</p>
                <button class="btn btn-light"
                    @click="$emit('eliminarCita')">Eliminar</button>
            </div>
        </div>
    </div>

</template>

<script>
export default {
    name: 'CardCita',
    props: {
        cita: Object,
    },
    data() {
        return {}
    }
}
</script>

<style scoped></style>