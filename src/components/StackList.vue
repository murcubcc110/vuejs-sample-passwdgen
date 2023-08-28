<template>
    <div>
        <input type="text" v-model="newTodo" />
        <button @click="addTodo">Stock</button>
        <ul>
            <li v-for="(todo, index) in todos" :key="index">
                {{ todo }}
                <button @click="removeTodo(index)" class="button-small">✕</button>
            </li>
        </ul>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref, watch } from 'vue';

export default defineComponent({
    props: ({
        stockValue: { type: String, required: true },
    }),
    setup(props) {
        const newTodo = ref(props.stockValue);
        const reloadKey = ref(0);
        const todos = ref<string[]>([]);

        function addTodo() {
            if (newTodo.value) {
                todos.value.push(newTodo.value);
                newTodo.value = '';
            }
        }

        function removeTodo(index: number) {
            todos.value.splice(index, 1);
        }

        watch(() => props.stockValue, () => {
            newTodo.value = props.stockValue;
            reloadKey.value++;
        })

        return {
            newTodo,
            todos,
            addTodo,
            removeTodo,
            reloadKey
        };
    }
});
</script>

<style scoped>
button {
    color: #fff;
    background-color: #eb6100;
    font-size: 0.5em;
}

.button-small {
    color: #fff;
    background-color: #eb6100;
    font-size: 0.2em;
}

li {
    text-align: left;
    padding: 0;
}
</style>