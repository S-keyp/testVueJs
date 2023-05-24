<script setup>
    import { ref } from 'vue';
    import { computed } from '@vue/reactivity';
    const count = ref(0)
    const color = computed(() => count.value > 3 ? 'green' : 'blue')

    defineProps({
        prefix: String
    })

    function handleClick(){
        count.value++
    }

</script>

<template>
    <p class="compteur">
        {{ prefix }} Compteur : {{ count }}
    </p>
    <p>
        <button @click="handleClick">
            Incrementer
        </button>
    </p>
</template>

<style scoped>
    .compteur{
        background-color: v-bind(color);
    }
</style>