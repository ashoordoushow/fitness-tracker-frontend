<script>
import axios from "axios";
import ExercisesIndex from "./ExercisesIndex.vue";
import ExercisesNew from "./ExercisesNew.vue";

export default {
  components: {
    ExercisesIndex,
    ExercisesNew
  },
  data: function () {
    return {
      exercises: [],
    };
  },
  created: function () {
    this.handleIndexExercises();
  },
  methods: {
    handleIndexExercises: function () {
      axios.get("http://localhost:3000/exercises.json").then((response) => {
        console.log("exercises index", response);
        this.exercises = response.data;
      });
    },
    handleCreateExercise: function (params) {
      axios
        .post("http://localhost:3000/exercises.json", params)
        .then((response) => {
          console.log("exercise create", response);
          this.exercises.push(response.data);
        })
        .catch((error) => {
          console.log("exercises create error", error.response);
        });
    },
  },
};
</script>

<template>
  <main>
    <ExercisesNew v-on:createExercise="handleCreateExercise" />
    <ExercisesIndex v-bind:exercises="exercises" />
  </main>
</template>

<style></style>

