<script>
export default {
  data: function () {
    return {
      newExerciseParams: {},
    };
  },
  methods: {
    handleSubmit: function () {
      this.$emit("createExercise", this.newExerciseParams);
      this.newExerciseParams = {};
    },
  },
};
</script>

<template>
  <div>
    <h1>New Exercise</h1>
    <form v-on:submit.prevent="handleSubmit">
      <div>
        Name:
        <input type="text" v-model="newExerciseParams.name" />
      </div>
      <div>
        Image_url:
        <input type="text" v-model="newExerciseParams.image_url" />
      </div>
      <div>
        Workout_id:
        <input type="text" v-model="newExerciseParams.workout_id" />
      </div>
      <div>
        Reps:
        <input type="text" v-model="newExerciseParams.reps" />
      </div>
      <div>
        Sets:
        <input type="text" v-model="newExerciseParams.sets" />
      </div>
      <button type="submit">Create exercise</button>
    </form>
  </div>
</template>

<style></style>