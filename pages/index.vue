<template>
  <div
    :class="menuActive ? '-locked' : ''"
    class="root"
    @touchmove="prevent">
    <div
      :class="menuActive ? '-active' : ''"
      class="menu">
      <div class="menu-btns">
        <a
          href="#"
          class="btn menu-btn">
          <span class="btn-text">Link</span>
        </a>
        <a
          href="#"
          class="btn menu-btn">
          <span class="btn-text">Link</span>
        </a>
        <a
          href="#"
          class="btn menu-btn">
          <span class="btn-text">Link</span>
        </a>
        <a
          href="#"
          class="btn menu-btn">
          <span class="btn-text">Link</span>
        </a>
      </div>
    </div>
    <div class="navbar">
      <span class="title">Austen Wade</span>
      <div class="hamburger-btn">
        <svg
          :class="menuActive ? '-active' : ''"
          class="ham hamRotate ham"
          viewBox="0 0 100 100"
          width="80"
          @click="hamburgerClick">
          <path
            class="line top"
            d="m 30,33 h 40 c 3.722839,0 7.5,3.126468 7.5,8.578427 0,5.451959 -2.727029,8.421573 -7.5,8.421573 h -20" />
          <path
            class="line middle"
            d="m 30,50 h 40" />
          <path
            class="line bottom"
            d="m 70,67 h -40 c 0,0 -7.5,-0.802118 -7.5,-8.365747 0,-7.563629 7.5,-8.634253 7.5,-8.634253 h 20" />
        </svg>
      </div>
    </div>
    <div class="main">
      <div class="hero">
        <img
          class="image"
          src="~/assets/wasatch-sky.jpeg">
      </div>
      <div class="section-tech">
        <h2 class="title">Tech that I use</h2>
        <div class="cards-wrapper">
          <div class="card-tech -frontend">
            <h3>Front End</h3>
            <ul>
              <li>Javascript</li>
              <li>CSS</li>
              <li>Webpack</li>
              <li>Vue</li>
              <li>React</li>
            </ul>
          </div>
          <div class="card-tech -backend">
            <h3>Back End</h3>
            <ul>
              <li>Java</li>
              <li>PHP</li>
              <li>Python</li>
              <li>AEM</li>
              <li>Wordpress</li>
            </ul>
          </div>
        </div>
      </div>
      <div class="section-companies">
        <h2 class="title">Companies that I've worked with</h2>
        <div class="company-logos">
          <div class="company-logo-wrapper adobe">
            <img
              src="~/assets/logos/adobe.png"
              alt="adobe"
              class="adobe">
          </div>
          <div class="company-logo-wrapper walmart">
            <img
              src="~/assets/logos/walmart.png"
              alt="walmart"
              class="walmart">
          </div>
          <div class="company-logo-wrapper chase">
            <img
              src="~/assets/logos/chase.png"
              alt="chase"
              class="chase">
          </div>
          <div class="company-logo-wrapper ingersollrand">
            <img
              src="~/assets/logos/ingersollrand.png"
              alt="ingersollrand"
              class="ingersollrand">
          </div>
        </div>
      </div>
      <div class="section-contact">
        <h2 class="title">Contact me today</h2>
        <div class="contact-link-wrapper">
          <div class="contact-link-item">
            <img
              src="~/assets/svg/email.svg"
              alt="email icon">
            <a
              class="contact-link email"
              href="mailto:austen.wade.ut@gmail.com">
              austen.wade.ut@gmail.com</a>
          </div>
          <div class="contact-link-item">
            <img
              src="~/assets/svg/phone.svg"
              alt="phone icon">
            <a
              class="contact-link phone"
              href="tel:801-989-2439">
              (801) 989-2439</a>
          </div>
        </div>
      </div>
      <div class="section-social">
        <h2 class="title">Find examples of my work here</h2>
        <div class="social-link-wrapper">
          <a
            class="card-linkedin"
            href="https://www.linkedin.com/in/austen-wade-3b723613b"
            target="_blank">
            <div class="social-image">
              <img
                class="image linkedin"
                src="~/assets/logos/linkedin.png"
                alt="linkedin">
            </div>
          </a>
          <a
            class="card-github"
            href="https://www.github.com/austen-wade"
            target="_blank">
            <div class="social-image">
              <img
                class="image github"
                src="~/assets/logos/github.png"
                alt="github">
            </div>
          </a>
          <a
            class="card-codepen"
            href="https://codepen.io/austen-wade/"
            target="_blank">
            <div class="social-image">
              <img
                class="image codepen"
                src="~/assets/logos/codepen.png"
                alt="codepen">
            </div>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      menuActive: false
    }
  },
  methods: {
    hamburgerClick() {
      if (this.menuActive) {
        this.menuActive = false
        document.documentElement.style.overflow = 'auto'
      } else {
        this.menuActive = true
        document.documentElement.style.overflow = 'hidden'
      }
    },
    prevent(e) {
      if (this.menuActive) {
        e.preventDefault()
        e.stopPropagation()
      }
    }
  }
}
</script>

<style lang="scss">
.cards-wrapper {
  display: flex;
  margin-top: 20px;

  .card-tech {
    flex: 1;
    text-align: center;

    ul {
      padding: 0;
      list-style: none;
    }
  }
}
.social-link-wrapper {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin-top: 20px;

  @include _600 {
    flex-direction: row;
    margin-top: 40px;
  }

  > [class^='card'] {
    flex: 1;
    border: 1px solid $lightGray;
    border-radius: 10px;
    box-shadow: 0px 6px 6px #ccc, 0px 6px 20px #ccc;
    margin: 20px;
    padding: 80px 20px;

    transition: 300ms transform;

    &:hover {
      transform: translateY(-5%);
    }

    @include _600 {
      margin: 0;

      & + [class^='card'] {
        margin-top: 35px;

        @include _600 {
          margin-top: 0;
          margin-left: 35px;
        }
      }
    }

    > .social-image {
      width: 100%;

      > .image {
        width: 100%;

        &.codepen {
          padding: 8px 0;
        }
      }
    }
  }
}
.root {
  height: 100%;
  width: 100%;
  overflow: hidden;

  &.-locked {
    overflow: hidden;
  }
}
.navbar {
  position: relative;
  width: 100%;
  max-width: 960px;
  margin: 0 auto;
  padding: 20px 20px;
  display: flex;
  align-items: center;
  height: 70px;
  z-index: 10;

  > .title {
    color: $black;
    font-size: 24px;
    margin-right: auto;
  }
  > .hamburger-btn {
    margin-left: auto;
  }
}
.main {
  margin: 0 auto;
  max-width: 960px;
}
.hero {
  > .image {
    width: 100%;
  }
}
.menu {
  height: 100vh;
  padding: 20px;
  width: 100%;
  background-color: $white;
  position: absolute;
  opacity: 0;
  pointer-events: none;
  transform: translateY(-20%);
  transition: opacity 1s, transform 1s;

  > .menu-btns {
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    > .menu-btn {
      display: block;
      position: relative;
      border: 1px solid $black;
      color: $black;
      padding: 15px;
      width: 200px;
      transition: color 500ms;
      text-align: center;
      text-decoration: none;
      overflow: hidden;

      > .btn-text {
        position: relative;
        z-index: 2;
      }

      & + .menu-btn {
        margin-top: 10px;
      }
      &:before {
        content: '';
        position: absolute;
        background-color: $black;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        transform: translateX(-100%);
        transition: transform 500ms;
      }

      &:hover {
        color: $white;

        &:before {
          transform: translateX(0%);
        }
      }
    }
  }

  &.-active {
    opacity: 1;
    pointer-events: all;
    transform: translateY(0%);
  }
}
[class^='section'] {
  padding: 40px 20px;

  @include _600 {
    padding: 40px 80px;
  }

  > .title {
    margin: 0 auto;
    font-weight: 200;
    color: $lightGray;
    text-align: center;
  }
}
.contact-link-wrapper {
  display: flex;
  flex-direction: column;

  @include _600 {
    margin-top: 20px;
    flex-direction: row;
  }

  > .contact-link-item {
    display: flex;
    flex: 1;
    margin-top: 20px;
    text-align: center;
    justify-content: center;
    align-items: center;

    > .contact-link {
      margin-left: 20px;
      text-decoration: none;

      &:hover {
        color: darkslateblue;
      }
    }
  }
}
.company-logos {
  display: flex;
  flex-wrap: wrap;

  > .company-logo-wrapper {
    flex: 1 100%;
    display: grid;
    align-content: center;
    padding: 30px;

    @include _400 {
      padding: 50px;
      flex: 1 50%;
    }
    @include _900 {
      flex: 1;
    }

    > img {
      width: 100%;
    }
  }
}
.ham {
  cursor: pointer;
  -webkit-tap-highlight-color: transparent;
  transition: transform 400ms;
  -moz-user-select: none;
  -webkit-user-select: none;
  -ms-user-select: none;
  user-select: none;
  width: 50px;
  height: 50px;

  > .top {
    stroke-dasharray: 40 160;
  }
  > .middle {
    stroke-dasharray: 40 142;
    transform-origin: 50%;
    transition: transform 400ms;
  }
  > .bottom {
    stroke-dasharray: 40 85;
    transform-origin: 50%;
    transition: transform 400ms, stroke-dashoffset 400ms;
  }

  &.-active {
    > .top {
      stroke-dashoffset: -64px;
    }
    > .middle {
      transform: rotate(90deg);
    }
    > .bottom {
      stroke-dashoffset: -64px;
    }
  }
}
.hamRotate.-active {
  transform: rotate(45deg);
}
.hamRotate180.-active {
  transform: rotate(180deg);
}
.line {
  fill: none;
  transition: stroke-dasharray 400ms, stroke-dashoffset 400ms;
  stroke: $black;
  stroke-width: 5.5;
  stroke-linecap: round;
}
</style>
