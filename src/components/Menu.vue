<template>
    <header>
        <div>
            <span>Series Break</span>
            <i class="fa-solid fa-dumbbell"></i>
        </div>
        <button disabled>Ativar modo escuro</button>
    </header>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';

    export default defineComponent({
        name: 'MenuC'
    })
</script>

<style scoped>
    header{
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 1rem;
        padding: 0.5rem 0;
    }
    div{
        display: flex;
        gap: 1rem;
    }
    span{
        font-size: 1.5rem;
    }
    i{
        font-size: 1.5rem;
    }
</style>