<template>
    <button class="btn">
        <slot></slot>
    </button>
</template>
  
<script>
export default {
    name: 'custom-button'
}
</script>
  
<style scoped>
.btn {
    margin-top: 15px;
    align-self: flex-end;
    padding: 10px 15px;
    background: aliceblue;
    color: #35656F;
    border: 2px solid aliceblue;
    border-radius: 10px;
}

.btn:hover {
    background-color: #6C80EF;
    color: aliceblue;

}
</style>