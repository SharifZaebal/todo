<script setup>
import { ref, onMounted } from "vue";
import jsonData from "./assets/tasks.json";
const getTasks = jsonData;

let status = false;
const completedTask = () => {
  if (status) {
    status = false;
  } else {
    status = true;
  }
  console.log(status);
};

</script>

<template>
  <header class="header">
    <h1 class="header__section-header">Ваши задачи на сегодня</h1>
  </header>
  <main class="main">
    <section class="section-tasks">
      <ul class="section-tasks__list">
        <li
          class="section-tasks__item"
          v-for="item of getTasks"
          :key="item.id"
          ref="tasksItem"
        >
          <h2 class="task-header">
            {{ item.title }}
          </h2>
          <div class="flex-jc-sb">
            <p class="task-description">{{ item.description }}</p>
            <input
              type="checkbox"
              ref="completedBtn"
              v-on:click="completedTask()"
            />
          </div>
        </li>
      </ul>
    </section>
  </main>
</template>

<style>
.flex-jc-sb {
  display: flex;
  justify-content: space-between;
}

.header {
  text-align: center;
  font-size: 50px;
  padding-top: 50px;

  margin-bottom: 40px;
}
.main {
  width: 700px;
  margin: 0 auto;
  font-size: 25px;
}

.section-tasks__item {
  padding: 10px;

  background-color: rgb(201, 201, 201);
  border-radius: 10px;

  color: #303030;
}
.section-tasks__item:not(:last-child) {
  margin-bottom: 20px;
}
</style>
