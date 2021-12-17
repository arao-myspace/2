<template>
    <div>
        <div class="item" v-bind:class="{
      completed: item.completed
    }">
            <h2>{{item.title}}</h2>
            <button v-if="!item.completed" v-on:click="removeItem">Zrobione</button>
        </div>
    </div>
</template>
<script>
    export default {
        props: ["item"],
        methods: {
            removeItem() {
            this.$emit('doneClicked', this.item.id) //emit tworzy nowy event i może przekazać parametr do komponentu nadrzędnego
        }}
    }
</script>