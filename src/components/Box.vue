<template>
    <div class="box has-text-weight-bold" :style="estilos">
        <slot />
    </div>
</template>

<script lang="ts">
import { defineAsyncComponent, defineComponent } from 'vue'

export default defineComponent ({
    name: 'box-style',
    data () {
        return {
            estilos: {
                backgroundColor: '#FAF0CA'
            }
        }
    }
})
</script>