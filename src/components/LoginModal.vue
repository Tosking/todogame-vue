<template>
    <div class="modal" v-if="show">
        <div class="modalContent">
            <slot>

            </slot>
        </div>
    </div>
</template>

<script>
export default {
    name: 'loginModal',
    props:{
        show: {
            type: Boolean,
            default: false
        }
    }

}
</script>

<style>
.modal {
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    background: rgba(100, 100, 100, 0.5);
    position: fixed;
    display: flex;
}
.modalContent {
    margin: auto;
    background-color: white;
    border-radius: 15px;
    min-width: 300px;
    min-height: 50px;
    padding: 10px;
}
</style>