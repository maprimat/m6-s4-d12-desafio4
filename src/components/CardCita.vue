<!-- TEMPLATE -->
<template>
    <div class="CardCita">
        <div class="card"
            :class="cita.gravedad == 'Baja' ? 'text-bg-success' : cita.gravedad == 'Media' ? 'bg-warning' : 'text-bg-danger'"
            style="">
            <div class="card-body">
                <h6 class="card-title fw-bold">Paciente</h6>
                <p class="card-text">{{ cita.paciente }}</p>
                <h6 class="card-title fw-bold">Fecha</h6>
                <p class="card-text">{{ cita.fecha }}</p>
                <h6 class="card-title fw-bold">Hora</h6>
                <p class="card-text">{{ cita.hora }}</p>
                <h6 class="card-title fw-bold">Motivo</h6>
                <p class="card-text">{{ cita.motivo }}</p>
                <a href="#" class="btn btn-primary" @click="$emit('EliminarCita')">Eliminar</a>
            </div>
        </div>
    </div>
</template>

<!-- SCRIPT -->
<script>
export default {
    name: "CardCita",
    props: {
        cita: Object,
    },
    data() {
        return {};
    },
};
</script>

<!-- STYLE -->
<style scope></style>