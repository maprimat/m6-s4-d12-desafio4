<!-- TEMPLATE -->
<template>
    <div id="app" class="container text-center">
        <main>

            <!-- TITLE -->
            <h1 class="fw-medium py-3">Calendario de citas médicas</h1>

            <!-- CONTAINER -->
            <form class="border rounded py-4" @submit.prevent="agregarCita">
                <div class="d-md-flex flex-wrap justify-content-around">

                    <!-- PACIENTE -->
                    <div>
                        <label
                            for=""
                            class="form-label"
                            :class="!cita.paciente ? 'text-danger fw-bold' : ''"
                            >Paciente:
                        </label>
                        <input
                            type="text"
                            class="form-control"
                            v-model="cita.paciente"
                        />
                    </div>

                    <!-- FECHA -->
                    <div>
                        <label
                            for=""
                            class="form-label"
                            :class="!cita.fecha ? 'text-danger fw-bold' : ''"
                        >
                            Fecha:
                        </label>
                        <input
                            type="date"
                            class="form-control"
                            v-model="cita.fecha"
                        />
                    </div>

                    <!-- HORA -->
                    <div>
                        <label
                            for=""
                            class="form-label"
                            :class="!cita.hora ? 'text-danger fw-bold' : ''"
                            >Hora:
                        </label>
                        <input
                            type="time"
                            class="form-control"
                            v-model="cita.hora"
                        />
                    </div>

                    <!-- GRAVEDAD -->
                    <div>
                        <label
                            for=""
                            class="form-label"
                            :class="!cita.gravedad ? 'text-danger fw-bold' : ''"
                            >Gravedad:
                        </label>
                        <select
                            name=""
                            id=""
                            class="form-select"
                            v-model="cita.gravedad"
                        >
                            <option
                                :value="gravedad"
                                v-for="(gravedad, index) in gravedades"
                                :key="index"
                            >
                                {{ gravedad }}
                            </option>
                        </select>
                    </div>

                    <!-- MOTIVO -->
                    <div>
                        <label
                            for=""
                            class="form-label"
                            :class="!cita.motivo ? 'text-danger fw-bold' : ''"
                            >Motivo:
                        </label>
                        <input
                            type="text"
                            class="form-control"
                            v-model="cita.motivo"
                        />
                    </div>
                </div>

                <!-- BOTON -->
                <div class="mt-4">
                    <button
                        type="submit"
                        class="btn btn-dark"
                        :disabled="
                            !cita.paciente ||
                            !cita.fecha ||
                            !cita.hora ||
                            !cita.gravedad ||
                            !cita.motivo
                        "
                    >
                        Agregar
                    </button>
                </div>
            </form>
            
            <!-- SECCIÓN CARD -->
            <div>
                <p class="text-danger my-4" v-if="citas.length < 1">
                    No hay citas registradas
                </p>
                <div v-else class="row g-3">
                    <div
                        class="col-12 col-md-6 col-lg-4 py-4"
                        v-for="(cita, index) in citas"
                        :key="index"
                    >
                        <CardCita
                            :cita="cita"
                            @EliminarCita="eliminarCitaHandler(index)"
                        />
                    </div>
                </div>
            </div>

        </main>
    </div>
</template>

<!-- SCRIPT -->
<script>
import CardCita from "./components/CardCita";
export default {
    name: "App",
    components: {
        CardCita,
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
            gravedades: ["Baja", "Media", "Alta"],
        };
    },
    methods: {
        agregarCita() {
            this.citas.push(this.cita);
            this.cita = {};
        },
        eliminarCitaHandler(index) {
            if (confirm("¿Desea eliminar esta cita?")) {
                this.citas.splice(index, 1);
            }
        },
    },
    computed: {},
};
</script>

<!-- STYLE -->
<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
}
</style>
