<template>
    <div>
        <label>
            <slot>デフォルト</slot>
        </label>
        <label>
            <input type="radio" :id="id" value="yes" v-model="value" @click="onClickRadio('yes')" />
            はい
        </label>
        <label>
            <input type="radio" :id="id" value="no" v-model="value" @click="onClickRadio('no')" />
            いいえ
        </label>
    </div>
</template>

<script lang="ts">
import { Ref, defineComponent, ref, watch ,computed} from 'vue';

export default defineComponent({
    props : ({
        id: { type: String, required: true },
        value: { type: String, default: "yes" },
    }),    
    setup(props, ctx ) {
        const id = ref(props.id);
        const value = ref(props.value);
        const selected = ref(0);

        function onClickRadio(e: string): void {
            ctx.emit("symbol-update",e);
        }

         return {
            id,
            value,
            selected,
            onClickRadio
        };
    },
});
</script>
