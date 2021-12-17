<template>
    <div>
        <div class="item">
            <input type="text" placeholder="todo" v-model="newItem" />
            <button v-on:click="addItem">Dodaj</button>
        </div>
        <ToDoItem v-for="item in items" v-bind:key="item.id" v-bind:item="item" 
        @doneClicked="removeItem"/>
    </div>
</template>

<script>
    import ToDoItem from './ToDoItem.vue'
    export default {
        components: {
            ToDoItem
        },
        data() {
            return {
                newItem: '',
                items: [{
                        id: '1',
                        title: 'Zrobić zakupy',
                        completed: true
                    },
                    {
                        id: '2',
                        title: 'Zagrać w grę',
                        completed: false
                    }
                ],
                counter: 0,
            }
        },
        methods: {
            greet() {
                alert('Hello!!!')
            },
            addItem() {
                if (this.newItem !== null || this.newItem !== undefined) {
                    this.counter++
                    this.items.push({
                        id: this.counter,
                        title: this.newItem,
                        completed: false
                    })
                }
                this.newItem = ''
            },
            removeItem(itemId) {
            const index = this.items.findIndex(el => el.id === itemId)
            this.items[index].completed = true
        }
        },
        created: function () {
            this.counter = this.items.length //init counter
        }
    }
</script>

<style>
    .item {
        border: 1px solid #cdcdcd;
        margin: 8px;
        padding: 10px;
    }

    .completed {
        opacity: 0.5;
    }

    .completed h2 {
        text-decoration: line-through;
    }
</style>