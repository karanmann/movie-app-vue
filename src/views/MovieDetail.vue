<template>
  <div class="movie-detail">
    <h2 >{{movie.Title}}</h2>
  </div>
</template>

<script>
import { ref, onBeforeMount } from "vue";
import { useRoute } from "vue-router";

export default {
  setup() {
    const movie = ref({});
    const route = useRoute();

    onBeforeMount(() => {
      fetch(
        `http://www.omdbapi.com/?apikey=${process.env.VUE_APP_OMDB_OPEN_API_TOKEN}&i=${route.params.id}&plot=full`
      )
        .then(res=> res.json())
        .then(data => {
					movie.value = data
					console.log(movie.value)
				});

      return {
        movie,
      };
    });
  },
};
</script>

<style lang="scss">

.movie-detail {
	color: white;
}
</style>
