<template>
    
    <div class="add-taks">
        <div class="add-btn" @click="toggleAddBtn">
            <img src="./../../assets/add.png" alt="">
        </div>
    </div>
</template>

<script>

    export default {
        data() {
            return{
            
            }
        },
        methods : {
            toggleAddBtn() {
                this.$emit('addTask')
            }
        }
    }
</script>

<style scoped>
    .add-btn{
        background-color: #00ff777e;
        width: 60px;
        height: 60px;
        border-radius: 50%;
        display: flex;
        justify-content: center;
        align-items: center;
        border: 1px solid white;
        cursor: pointer;
    }

    img{
        width: 35px;
        height: 35px;
    }
</style>