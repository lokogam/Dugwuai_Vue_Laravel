<template>
   <div class="wrapper">
       <narvar-admin/>
       <div class="main">
           <hearder-admin>
               
           </hearder-admin>
       </div>
   </div>
</template>

<script>
    import { defineComponent } from 'vue'
import NarvarAdmin from '../Admin/NarvarAdmin.vue'
import HearderAdmin from '../Admin/HearderAdmin.vue'

    export default defineComponent({
        components: {
    NarvarAdmin,
    HearderAdmin
},
    })
</script>