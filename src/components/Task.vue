<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
        <h3>
            {{ task.text }}

            <i class="fas fa-times" @click="$emit('delete-task',task.id)"></i>
        </h3>

        <p>{{ task.day }}</p>
    </div>
</template>

<script>

export default {
    name: 'Task',
    props: {
        task: Object
    }
}
</script>

<style scoped>
    .task {
        background: #dadada;
        padding: 10px 20px;
        margin: 5px;
        text-align: left;
    }

    .task h3 {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .fas {
        color: red;
    }

    .task.reminder {
        border-left: 4px solid green;
    }
</style>