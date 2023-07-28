<template>
    <div class="dialog" v-if="show" @click.stop="hideDialog">
        <div @click.stop class="dialog__content">
            <slot></slot>
        </div>
    </div>
</template>
  
<script>

import toggleMixin from "@/mixins/toggleMixin";

export default {
    name: 'dialog-window',
    mixins: [toggleMixin],
    mounted() {
        console.log('dialog mounted')
    }
}
</script>
  
<style scoped>
.dialog {
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    background: rgba(62, 85, 117, 0.7);
    position: fixed;
    display: flex;
}

.dialog__content {
    margin: auto;
    min-height: 50px;
    min-width: 300px;
}
</style>