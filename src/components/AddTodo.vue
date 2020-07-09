<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="title">
        <button type="submit">Добавить</button>
    </form>
</template>

<script>
    export default {
        data() {
            return {
                title: ''
            }
        },
        methods: {
            onSubmit() {
                if (this.title.trim()) {
                    const newTodo = {
                        id: Date.now(),
                        title: this.title,
                        completed: false
                    };

                    this.$emit('add-todo', newTodo);
                    this.title = '';
                }
            }
        }
    }
</script>

<style scoped>
    form {
        display: flex;
    }

    input {
        max-width: 150px;
        margin-right: 5px;

        font-size: 1rem;
    }

    button {
        flex-shrink: 0;
        font-size: 1rem;
        line-height: 1rem;
    }
</style>