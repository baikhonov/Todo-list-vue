<template>
    <li>
        <span v-bind:class="{done: todo.completed}">
            <input type="checkbox"
                    v-on:change="todo.completed = !todo.completed">
            <strong>{{index + 1}}</strong>
            {{todo.title | uppercase}}
        </span>
        <button class="rm"
                v-on:click="$emit('remove-todo', todo.id)">&times;
        </button>
    </li>
</template>

<script>
    export default {
        props: {
            todo: {
                type: Object,
                required: true
            },
            index: Number
        },
        filters: {
            uppercase(value) {
                return value.toUpperCase();
            }
        }
    }
</script>

<style scoped>
    li {
        display: flex;
        align-items: flex-start;
        justify-content: space-between;

        padding: 0.5rem 2rem;
        margin-bottom: 1rem;
        border: 1px solid #cccccc;
    }

    span {
        text-align: left;
    }

    .rm {
        font-weight: 700;

        color: #ffffff;
        background-color: red;
        border: 1px solid red;
        border-radius: 50%;
        cursor: pointer;
    }

    input {
        margin-right: 1rem;
    }

    .done {
        text-decoration: line-through;
    }
</style>