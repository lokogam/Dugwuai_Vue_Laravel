<template>
        <nav class="navbar navbar-expand navbar-light navbar-bg">
            <a class="sidebar-toggle js-sidebar-toggle">
                <i class="hamburger align-self-center"></i>
            </a>

            <div class="navbar-collapse collapse">
                <ul class="navbar-nav navbar-align">
                    
                    <li class="nav-item dropdown">
                        <a class="nav-link dropdown-toggle  d-sm-inline-block" data-bs-toggle="dropdown">
                            <div class="row">
                                <div class="col-6">
                                    <img class="h-8 w-8 rounded-full object-cover" :src="$page.props.user.profile_photo_url" :alt="$page.props.user.name" />
                                </div>
                                <div class=" col-6">
                                    <span class="text-dark">{{ $page.props.user.name }}</span>
                                </div>
                            </div>
                        </a>

                        <div class="dropdown-menu dropdown-menu-end">
                            <a class="dropdown-item" href="pages-profile.html"
                                ><i
                                    class="align-middle me-1"
                                    data-feather="user"
                                ></i>
                                Profile</a
                            >
                            
                            <div class="dropdown-divider"></div>
                            <a class="dropdown-item" href="index.html"
                                ><i
                                    class="align-middle me-1"
                                    data-feather="settings"
                                ></i>
                                Settings & Privacy</a
                            >

                            <div class="dropdown-divider"></div>
                                <!-- Authentication -->
                                <form @submit.prevent="logout">
                                    <jet-dropdown-link as="button">
                                        Log Out
                                    </jet-dropdown-link>
                                </form>
                        </div>
                    </li>
                </ul>
            </div>
        </nav>
</template>

<script>
    import { defineComponent } from 'vue'
    import JetDropdownLink from '@/Jetstream/DropdownLink.vue'

    export default defineComponent({
        props: {
        },

        components: {
            JetDropdownLink,

        },

        methods: {
            logout() {
                this.$inertia.post(route('logout'));
            },
        }
    })
</script>
