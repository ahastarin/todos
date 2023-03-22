<template>
    <div v-if="isAdding">
        <AddModal @addTask="toggleAddBtn" :total="total" @increaseTotal="increaseTotal"/>
    </div>
    <div class="header">
        <h1>Todos</h1>
        <div class="content">
            <Date/>
            <p>{{ total }} Tasks</p>
            <AddTask @addTask="toggleAddBtn" @click="stopScroll"/>
        </div>
    </div>
</template>

<script>
    import Date from "./DateView.vue";
    import AddTask from "./AddTaskView.vue";
    import AddModal from './../../components/AddModal.vue';

    export default {
        props: ['total'],
        components: {
            Date, AddTask, AddModal
        },
        data () {
            return {
                isAdding: false            }
        },
        methods: {
            toggleAddBtn() {
                this.isAdding = !this.isAdding
            },
            stopScroll() {
                document.body.classList.add('stop-scrolling')
            },
            increaseTotal() {
                this.$emit('increaseTotal')
            },
            reloadFetch() {
                this.$emit('reloadFetch')
            }
        }
    }
</script>

<style scoped>

    .content{
        display: flex;
        width: 80%;
        margin: auto;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    h1{
        font-size: 5rem;
        color: #00FF75;
        margin-bottom: 50px;
    }
</style>