<template>
    <button @click="addTask()" class="btn" :style="{ background: color }">
        {{ text }}
    </button>
</template>


<script>
export default {
    name: 'Button',
    props: {
        text: String,
        color: String
    },
    methods: {
        addTask() {
            this.$emit('btn-click')
        }
    }
}
</script>

<style scoped>
    
</style>