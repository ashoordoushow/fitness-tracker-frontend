<script>
import axios from "axios";
import ExercisesIndex from "./ExercisesIndex.vue";

export default {
  components: {
    ExercisesIndex,
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
  },
};
</script>

<template>
  <main>
    <ExercisesIndex v-bind:exercises="exercises" />
  </main>
</template>

<style></style>


<!-- { id: 1, workout_id: 1, name: "Bench", reps: 10, sets: "3 sets of 10", image_url: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRgy5RWhaieyrevjvS6ErgThrTBiYQL44cfTA&s"},
        { id: 2, workout_id: 2, name: "Squat", reps: 5, sets: "3 sets of 5", image_url: "https://www.lifefitness.com/Kentico13CoreBase/media/LFMedia/LifeFitnessImages/MediaSync/332-687-hammerstrenght-olympic-squat-rack-l.png?h=630&w=1200"} -->