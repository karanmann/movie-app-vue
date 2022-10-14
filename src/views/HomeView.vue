<template>
  <div class="home">
    <div class="feature-card">
      <router-link to="/movie/tt0409591">
        <img
          class="feature-card__image"
          src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fimages2.alphacoders.com%2F445%2Fthumb-1920-445151.jpg&f=1&nofb=1&ipt=405fc20b01a316e8bcca46c382277e3440996290035f75678118e77e2b81908e&ipo=images"
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
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "HomeView",
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
      left:0;
      right: 0;
      bottom: 0;
      background-color: rgba(0, 0, 0, 0.8);
      padding: 1.2rem;
      z-index: 1;
    }

    h3,p {
      color: white;
    }

    h3 {
      margin-bottom: 1rem;
    }
  }
}
</style>
