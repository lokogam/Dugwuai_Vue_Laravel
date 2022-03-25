<template>
    <div class="wrapper">
        <narvar-admin></narvar-admin>
        <div class="main">
            <hearder-admin></hearder-admin>
            <main class="content">
                    <h1 class="h3 mb-3">Usuarios</h1>
                    <div class="card ">
                        <dir class="card-body">
                            <div class="mb-3">
                                <Link
                                    :href="route('user.create')"
                                    class="btn btn-info"
                                >
                                    Agreagar
                                </Link>
                            </div>
                            <table class="table table-striped table-hover">
                                <thead>
                                    <tr>
                                        <th>#</th>
                                        <th>foto</th>
                                        <th>Nombre</th>
                                        <th>Correo</th>
                                        <th>Assignacion</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr
                                        v-for="user in users.data"
                                        :key="user.id"
                                    >
                                        <td>{{ user.id }}</td>
                                        <td><img class="h-10 w-10 rounded-full object-cover" :src="user.profile_photo_url" :alt="$page.props.user.name" /></td>
                                        <td>{{ user.name }}</td>
                                        <td>{{ user.email }}</td>
                                        <td>Editar / 
                                            <button class="btn btn-danger" @click.prevent="eliminarUsuario(user.id)">
                                                Eliminar
                                            </button>
                                        </td>
                                    </tr>
                                </tbody>
                            </table>
                        </dir>
                        <div class="card-footer">
                            <paginator :paginator="users"></paginator>
                        </div>
                    </div>
            </main>
        </div>
    </div>
</template>

<script>
import { defineComponent } from "vue";
import NarvarAdmin from "@/Admin/NarvarAdmin.vue";
import HearderAdmin from "@/Admin/HearderAdmin.vue";
import Paginator from "@/Components/Paginator";
import { Link } from "@inertiajs/inertia-vue3";
import { Inertia } from "@inertiajs/inertia";

export default defineComponent({
    props: {
        users: Object,
    },
    components: {
        NarvarAdmin,
        HearderAdmin,
        Paginator,
        Link,
    },
    
    eliminarUsuario(id){
        Inertia.delete(route('usuarios.destroy', id))
    }
});
</script>
