<template>
  <nav :class="[scrollPosition > nextSection ? 'scroll-nav' : 'top-nav']">
    <div class="logo">
      <span>
        <router-link to="/">{{ logo }}</router-link>
      </span>
    </div>
    <div class="link">
      <a
        href="https://drive.google.com/file/d/1qXrrO5U5KAOKftazhOIStgQj3enIB1zM/view?usp=sharing"
        target="_blank"
      >
        <i class="fa fa-file-pdf-o" aria-hidden="true"></i>
      </a>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Navigation",
  data() {
    return {
      logo: "M",
      scrollPosition: 0,
      nextSection: 0
    };
  },
  mounted() {
    window.addEventListener("scroll", this.updateNavScroll);
  },
  methods: {
    updateNavScroll() {
      this.scrollPosition = window.scrollY;
      this.nextSection = document.querySelector("#tabs").offsetTop;
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/main.scss";

nav {
  width: 100vw;
  height: 10vh;
  position: fixed;
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: 300ms;
  z-index: 999;
}

.logo {
  font-size: 5vh;
  margin-left: 30px;
  outline: none;
  a {
    font-family: $font-stack-logo;
  }
}

.link {
  margin-right: 30px;
  font-family: "Helvetica", sans-serif;
  a {
    font-size: 4vh;
    transition: 100ms ease-in-out;
  }
}

.scroll-nav {
  background-color: $secondary-color;
  box-shadow: 0 5px 5px -6px $main-color;
  span {
    a {
      color: $accent-color-secondary;
      transition: 500ms ease-in-out;
      &:hover {
        transform: rotate(180deg);
        font-size: 6vh;
      }
    }
  }
  .link {
    a {
      display: inline-block;
      transition: 300ms;
      &:hover {
        font-size: 5vh;
        color: $accent-color-secondary;
      }
    }
  }
}

.top-nav {
  background-color: $main-color;
  span a {
    color: $secondary-color;
    transition: 500ms ease-in-out;
    &:hover {
      transform: rotate(180deg);
      font-size: 6vh;
    }
  }
  .link {
    a {
      display: inline-block;
      color: $secondary-color;
      transition: 300ms;
      &:hover {
        font-size: 5vh;
        color: $secondary-color;
      }
    }
  }
}
</style>
