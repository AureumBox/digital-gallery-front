<script lang="ts">
import { Divider, Panel } from 'primevue';
import { defineComponent } from 'vue';

export default defineComponent({
    components: {
        Divider,
        Panel
    },
    data() {
        return {
        }
    },
    methods: {
    },
})

</script>

<template>
    <div>
        <Panel header="Header" class="comment">
            <p class="m-0">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut
            </p>
        </Panel>
    </div>
</template>

<style scoped>
.comment {
    margin: 5px;
}
</style>
