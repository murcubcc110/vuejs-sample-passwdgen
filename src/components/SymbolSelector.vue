<template>
    <div>
        <label>
            <slot>デフォルト</slot>
        </label>
        <label>
            <input type="radio" :id="id" value="yes" v-model="value" @click="$emit('symbol-update', 'yes')" />
            はい
        </label>
        <label>
            <input type="radio" :id="id" value="no" v-model="value" @click="$emit('symbol-update', 'no')" />
            いいえ
        </label>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
    props : ({
        id: { type: String, required: true },
        value: { type: String, default: "yes" },
    }),    
    setup(props) {
        const id = ref(props.id);
        const value = ref(props.value);
        const selected = ref(0);
        return {
            id,
            value,
            selected,
        };
    },
});
</script>
