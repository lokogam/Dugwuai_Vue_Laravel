<template>
    <div>
        <nav id="sidebar" class="sidebar js-sidebar">
            <div class="sidebar-content js-simplebar">
                <a class="sidebar-brand" >
                    <span class="align-middle">Dugwuai</span>
                </a>

                <ul class="sidebar-nav">
                    
                    <li class="sidebar-header">
						Modulos
					</li>

                    <li class="sidebar-item" :class="{ 'active': $page.url.startsWith('/user') }">
                        <Link :href="route('user.index')" class="sidebar-link">
                            <span class="align-middle">Usuarios</span>
                        </Link>
                    </li>

                </ul>
            </div>
        </nav>
    </div>
</template>

<script>
import { defineComponent } from 'vue'
import JetDropdownLink from '@/Jetstream/DropdownLink.vue'
import { Head, Link } from '@inertiajs/inertia-vue3';
export default defineComponent({
    components: {
        Link,
        JetDropdownLink,
    },
});
</script>

