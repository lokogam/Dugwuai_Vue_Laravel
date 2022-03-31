<template>
    <div class="wrapper">
        <NarvarAdmin></NarvarAdmin>
        <div class="main">
            <HearderAdmin></HearderAdmin>
            <main class="content">
                <h1 class="h3 mb-3">Agregar Usuarios</h1>
                <div class="card">
                    <form @submit.prevent="submit">
                        <div class="row py-4">
                            <div class="col-0 col-sm-1 col-md-1" ></div>
                            <div class="col-12 col-sm-10 col-md-10">
                                <div class="card">
                                    <div class="card-header">
                                        <h5 class="card-title mb-0">Nombre</h5>
                                    </div>
                                    <div class="card-body">
                                        <input
                                            type="text"
                                            class="form-control"
                                            placeholder="Escribe tu nombre"
                                            v-model="form.name"
                                        />
                                        <div class="text-danger">
                                            {{ errors.name }}
                                        </div>
                                    </div>
                                </div>

                                <div class="card">
                                    <div class="card-header">
                                        <h5 class="card-title mb-0">Correo</h5>
                                    </div>
                                    <div class="card-body">
                                        <input
                                            type="text"
                                            class="form-control"
                                            placeholder="Escribe tu correo"
                                            v-model="form.email"
                                        />
                                        <div class="text-danger">
                                            {{ errors.email }}
                                        </div>
                                    </div>
                                </div>

                                <div class="card">
                                    <div class="card-header">
                                        <h5 class="card-title mb-0">
                                            Password
                                        </h5>
                                    </div>
                                    <div class="card-body">
                                        <input
                                            type="password"
                                            class="form-control"
                                            placeholder="Escribe tu password"
                                            v-model="form.password"
                                        />
                                        <div class="text-danger">
                                            {{ errors.password }}
                                        </div>
                                    </div>
                                </div>


                                <input
                                    type="submit"
                                    class="btn btn-info m-4"
                                    value="Guardar"
                                />
                                <Link
                                    :href="route('user.index')"
                                    class="btn btn-secondary"
                                >
                                    Regresar
                                </Link>
                            </div>
                            <div class="col-0 col-sm-1 col-md-1"></div>
                        </div>
                    </form>
                </div>
            </main>
        </div>
    </div>
</template>

<script>
import { Link,} from "@inertiajs/inertia-vue3";
import { Inertia } from "@inertiajs/inertia";
import { defineComponent } from "vue";
import NarvarAdmin from "../../Admin/NarvarAdmin.vue";
import HearderAdmin from "../../Admin/HearderAdmin.vue";

export default defineComponent({
    props: ["errors"],
    data() {
        return {
            form: {
                name: "",
                email: "",
                password: "",
            },
        };
    },
    components: {
        NarvarAdmin,
        HearderAdmin,
        Link,
    },
    methods: {
        submit() {
            Inertia.post(route("user.store"), this.form);
        },
        cleanForm: function () {
            this.form.name = "";
            this.form.email = "";
            this.form.password = "";
        },
    },
});
</script>
