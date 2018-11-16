<template>
  <div
    :class="menuActive ? '-locked' : ''"
    class="root"
    @touchmove="prevent">
    <OverlayMenu
      :menu-active="menuActive" />
    <Navbar
      :menu-active="menuActive"
      @menuOpen="openMenu"
      @menuClose="closeMenu" />
    <div class="main">
      <hero />
      <Section title="Tech that I use">
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
      </Section>
      <Section title="Companies that I've worked with">
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
      </Section>
      <Section title="Contact me today">
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
      </Section>
      <Section title="Examples of my work">
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
      </Section>
    </div>
  </div>
</template>

<script>
import navbar from '~/components/navbar.vue'
import menu from '~/components/menu.vue'
import hero from '~/components/hero.vue'
import section from '~/components/section.vue'

export default {
  components: {
    Navbar: navbar,
    OverlayMenu: menu,
    hero: hero,
    Section: section
  },
  data: function() {
    return {
      menuActive: false
    }
  },
  methods: {
    openMenu: function() {
      this.menuActive = true
      document.documentElement.style.overflow = 'hidden'
    },
    closeMenu: function() {
      this.menuActive = false
      document.documentElement.style.overflow = 'auto'
    },
    prevent: function(e) {
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
.main {
  margin: 0 auto;
  max-width: 960px;
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
      // filter: grayscale(100%);
      width: 100%;
    }
  }
}
</style>
