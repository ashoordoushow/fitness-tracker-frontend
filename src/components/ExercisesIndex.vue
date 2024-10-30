<script>
export default {
  props: {
    exercises: Array,
  },
};
</script>

<template>
  <div>
    <h1>All exercises</h1>
    <div v-for="exercise in exercises" v-bind:key="exercise.id">
      <h2>{{  exercise.name }}</h2>
      <img v-bind:src="exercise.image_url" />
      <p>Reps: {{ exercise.reps }}</p>
      <p>Sets: {{ exercise.sets }}</p>
      <p>Workout_id: {{ exercise.workout_id }}</p>
    </div>
  </div>
</template>

<style></style>