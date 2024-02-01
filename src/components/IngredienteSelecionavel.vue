<script lang="ts">
    import Tag from './Tag.vue';

    export default {
        data() {
            return {
                selecionado: false
            }
        },
        props: {
            ingrediente: { type: String, required: true }
        },
        components: { Tag },
        methods: {
            aoClicar() {
                this.selecionado = !this.selecionado
                
                if (this.selecionado) {
                    this.$emit('adicionarIngrediente', this.ingrediente);
                }
                else {
                    this.$emit('removerIngrediente', this.ingrediente);
                }
            }
        },
        emits: ['adicionarIngrediente', 'removerIngrediente']
    }
</script>

<template>
    <button 
        @click="aoClicar()" 
        class="ingrediente"
        type="button"
    >
        <Tag :texto="ingrediente" :ativa="selecionado"/>
    </button>
</template>

<style scoped>
.ingrediente {
    cursor: pointer;
}
</style>