<template>
    <div class="add-modal" >
        <form>
            <input v-model="task" type="text">
            <button type="submit" class="add" @click="submit();startScroll();toggleAddBtn()">Add Task</button>
            <button class="cancel" @click="toggleAddBtn();startScroll()">Cancel</button>
        </form>
    </div>
</template>

<script>

    export default {
        props: ['total'],
        data() {
            return{
                task: '',
            }
        },
        methods: {
            toggleAddBtn() {
                this.$emit('addTask')
            },
            startScroll() {
                document.body.classList.remove('stop-scrolling')
            },
            submit() {
                this.$emit('increaseTotal')

                let newTasks = {
                    id: this.total + 1,
                    task: this.task
                }

                fetch('http://localhost:3000/tasks', {
                    method: 'POST',
                    body: JSON.stringify(newTasks),
                    Accept: 'application.json',
                    headers: {"Content-type": "application/json"}
                })
                .then(response => response.json())
                .then(json => console.log(json))
                .catch(err => console.log(err))

                this.$route.push()
            },  
        }
    }
</script>

<style scoped>
    .add-modal{
        /* background-color: rgba(0, 0, 0, 0.473); */
        backdrop-filter: blur(10px);
        position: fixed;
        z-index: 9999;
        width: 100%;
        height: 100%;
        overflow: hidden;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    form{
        width: 50%;
    }

    input{
        width: 100%;
        height: 70px;
        padding: 20px;
        font-size: 2rem;
        background-color: #ffffff3a;
        color: white;
        border-radius: 15px;
        border: none;
        outline: none;
        margin-bottom: 30px;
    }

    button{
        outline: none;
        border: none;
    }

    .add{
        background-color: #00FF75;
        font-size: 1.5rem;
        padding: 10px;
        border-radius:10px;
        cursor: pointer;
        margin-right: 30px;
    }

    .cancel{
        background-color: #a0a0a0;
        font-size: 1.5rem;
        padding: 10px;
        border-radius:10px;
        cursor: pointer;
    }
</style>