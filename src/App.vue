<template>
  <div id="app" :class="{'theme-dark': nightMode}">
    <div class="container">
      <nav>
        <i class="fas fa-sun icon-sun" v-if="nightMode" @click="nightMode = !nightMode"></i>
        <i class="fas fa-moon icon-moon" v-else @click="nightMode = !nightMode"></i>
      </nav>
      <article>
        <img src="./assets/test-image.jpg" alt="">
        <p>
          Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.
        </p>
      </article>
    </div>
  </div>
</template>

<script>
  export default {
    data: () => {
      return {
        nightMode: false
      }
    },
    watch: {
      nightMode: function() {
        localStorage.setItem("nightMode", JSON.stringify(this.nightMode));
      }
    },
    created() {
      this.nightMode = JSON.parse(localStorage.getItem("nightMode"));
    }
  }
</script>

<style lang="scss">
  @import url('https://use.fontawesome.com/releases/v5.8.1/css/all.css');

  body {
    padding: 0;
    margin: 0;
  }

  #app {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 1rem;
    width: calc(100% - 20px);
    min-height: 100vh;
    padding: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: all .5s ease-in-out;

    color: #333;
    background-color: #efefef;

    .container {
      max-width: 550px;

      nav {
        position: relative;
        height: 50px;

        i {
          position: absolute;
          top: 10px;
          right: 10px;
          font-size: 1.6rem;
          cursor: pointer;
        }

        .icon-sun {
          color: #FCDA5F;
        }
        .icon-moon {
          color: #041B37;
        }
      }

      article {
        position: relative;
        padding: 10px;
        background-color: #fff;
        border: 1px solid #ccc;

        img {
          max-width: 100%;
          height: auto;
        }

        p {
          padding: 10px;

          &::first-letter {
              float: left;
              font-size: 4rem;
              line-height: .8;
              padding: 0 10px 0 0;
          }
        }
      }
    }

    &.theme-dark {
      color: #efefef;
      background-color: #333;

      article {
        background-color: #222;
        border: 1px solid #555;
      }
    }
  }
</style>
