<script>
import axios from "axios";
import ExercisesIndex from "./ExercisesIndex.vue";
import ExercisesNew from "./ExercisesNew.vue";
import Modal from "./Modal.vue";
import ExercisesShow from "./ExercisesShow.vue"

export default {
  components: {
    ExercisesIndex,
    ExercisesNew,
    Modal,
    ExercisesShow,
  },
  data: function () {
    return {
      exercises: [],
      currentExercise: {},
      isExercisesShowVisible: false,
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
    handleShowExercise: function (exercise) {
      console.log("handleShowExercise", exercise);
      this.currentExercise = exercise;
      this.isExercisesShowVisible = true;
    },
    handleClose: function () {
      this.isExercisesShowVisible = false;
    },
  },
};
</script>

<template>
  <main>
    <ExercisesNew v-on:createExercise="handleCreateExercise" />
    <ExercisesIndex v-bind:exercises="exercises" v-on:showExercise="handleShowExercise" />
    <Modal v-bind:show="isExercisesShowVisible" v-on:close="handleClose">
      <ExercisesShow v-bind:exercise="currentExercise" />
    </Modal>
  </main>
</template>

<style></style>

