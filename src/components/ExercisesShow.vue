<script>
export default {
  props: {
    exercise: Object,
  },
};
</script>

<template>
  <div>
    <h1>Exercise information</h1>
    <p>Name: {{ exercise.name }}</p>
    <p>Image_url: {{ exercise.image_url }}</p>
    <p>Reps: {{ exercise.reps }}</p>
    <p>Sets: {{ exercise.sets }}</p>
    <p>Workout_id: {{ exercise.workout_id }}</p>
  </div>
</template>

<style></style>