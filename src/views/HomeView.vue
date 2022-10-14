<template>
  <div class="home">
    <div class="feature-card">
      <router-link to="/movie/tt0409591">
        <img
          class="feature-card__image"
          src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fcdn5.vectorstock.com%2Fi%2F1000x1000%2F59%2F39%2Fnow-showing-movie-theater-banner-vector-3525939.jpg&f=1&nofb=1&ipt=f4b93a6bbf50d541a6418b8d5313d86a7cc4a5a5ddc7d7a8f7c8bc44abec56fb&ipo=images"
          alt="movie-collarge"
        />
        <div class="detail">
          <h3>Movie Name</h3>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Eum
            cupiditate laborum, excepturi asperiores nisi dolor sit assumenda
            tempora quibusdam doloremque similique fugiat animi, a voluptate
            tenetur nostrum voluptates id quidem.
          </p>
        </div>
      </router-link>
    </div>
    <form @submit.prevent="SearchMovies()" class="search-box">
      <input type="text" placeholder="What are you looking for?" v-model="search"/>
      <input type="submit" value="Search" />
    </form>
    <div class="movies-list">
      <div class="movie" v-for="movie in movies" :key="movie.imdbID">
        <router-link v-bind:to="'/movie/' + movie.imdbID" class="movie-link">
          <div class="product-image">
            <img :src="movie.Poster" alt="movie oposter">
            <div class="type">{{(movie.Type.toUpperCase())}}</div>
            <div class="detail">
              <p>{{movie.Year}}</p>
              <h2>{{movie.Title}}</h2>
            </div>
          </div>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import { ref } from 'vue';

export default {
  name: "HomeView",
  setup() {
    const search = ref("");
    const movies = ref([]);

    const SearchMovies = () => {
      if (search.value != "") {
        fetch(`http://www.omdbapi.com/?apikey=${process.env.VUE_APP_OMDB_OPEN_API_TOKEN}&s=${search.value}`)
        .then( res => res.json())
        .then(data => {
          movies.value = data.Search
          search.value = ""
        })
      }
    }
    return {
      search,
      movies,
      SearchMovies
    }
  }
};
</script>

<style lang="scss">
.home {
  .feature-card {
    position: relative;

    .feature-card__image {
      display: block;
      height: 25rem;
      width: 100%;
      object-fit: cover;

      position: relative;
      z-index: 0;
    }

    .detail {
      position: absolute;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: rgba(0, 0, 0, 0.8);
      padding: 1.2rem;
      z-index: 1;

      h3,
      p {
        color: white;
      }

      h3 {
        margin-bottom: 1rem;
      }
    }
  }

  .search-box {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 1.2rem;

    input {
      display: block;
      appearance: none;
      border: none;
      outline: none;
      background: none;

      &[type="text"] {
        width: 100%;
        color: white;
        background-color: #496583;
        font-size: 20px;
        padding: 10px 16px;
        border-radius: 8px;
        margin-bottom: 15px;
        transition: 0.4s;

        &::placeholder {
          color: #f3f3f3;
        }

        &::focus {
          box-shadow: 0px 3px 6px rgba (0, 0, 0, 0.2);
        }
      }

      &[type="submit"] {
        width: 100%;
        max-width: 300px;
        background-color: #42B883;
        padding: 16px;
        border-radius: 8px;
        color: #FFF;
        font-size: 20px;
        text-transform: uppercase;
        transition: 0.4s;
        &:active {
          background-color: #3B8070;
        }
      }
    }
  }

  .movies-list {
    display: flex;
    flex-wrap: wrap;
    margin: 0 8px;
    justify-content: center;

    .movie {
      max-width: 30%;
      height:100%;
      flex: 1 1 60%;
      padding: 16px 8px;

      .movie-link {
        display: flex;
        flex-direction: column;
        height: 100%;

        .product-image {
          position: relative;
          display:block;

          img {
            display: block;
            width: 100%;
            height: 275px;
            object-fit: cover;
          }

          .type {
            position: absolute;
            padding: 8px 16px;
            background-color: #42b883;
            color: white;
            bottom: 86px;
            left: 0;
          }
        }

        .detail {
          background-color: #496583;
          padding: 16px 8px;
          flex: 1 1 100%;
          border-radius: 0 0 0 8px;

          p {
            color: #aaa;
            font-size: 14px;
          }

          h2 {
            color: #fff;
            font-weight: 600;
            font-size: 18px;
          }
        }
      }
    }
  }
}
</style>
