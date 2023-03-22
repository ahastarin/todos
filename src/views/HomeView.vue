<template>
  <div class="home">
    <div class="tasks">
      <div v-for="task in tasks" :key="task.id">
        <div class="task">
          <div class="task-done-btn"></div>
          <p>{{ task.task }}</p>
          <img src="./../assets/delete.png" alt="">
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'HomeView',
  components: {

  },
  data() {
    return {
      tasks : undefined,
      total : undefined
    }
  },
  mounted() {
    fetch('http://localhost:3000/tasks')
      .then((res) => res.json())
      .then((data) => this.tasks = data)
      .then((data) => this.total = data.length)
  }
}
</script>

<style scoped>
  .home{
    padding-bottom: 30px;
  }
  .task{
    width: 70%;
    border: 1px solid white;
    padding: 20px;
    border-radius: 10px;
    display: flex;
    align-items: center;
    margin: 30px auto;
    position: relative;
  }

  .task-done-btn{
    border: 1px solid white;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    margin-right: 50px;
    cursor: pointer;
  }

  .task-done-btn:hover{
    background-color:  #00ff777e;;
  }

  p{
    height: fit-content;
    font-size: 1.5rem;
  }

  img{
    position: absolute;
    right: 20px;
    width: 40px;
  }
</style>
