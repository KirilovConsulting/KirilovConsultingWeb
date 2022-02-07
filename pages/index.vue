<template>
  <div>
    <div
      class="container-fluid bg-img1 size1 overlay1 m-0"
      style="background-image: url('img/landing.jpg');"
    >
      <div style="position: relative" class="ml-md-5 row pt-5">
        <div
          class="col-md-5 col-12 text-center display-2 display-md-2 d-flex"
        >
            <!-- src="/logo/vector/default-monochrome.svg" -->
          <img
            src="/img/logo.png"
            class="navbar-brand-img d-none d-sm-block logo"
            alt="Kirilov Consulting"
          />
          <img
            src="/logo/vector/isolated-monochrome-white.svg"
            class="navbar-brand-img img-fluid logo-text"
            alt="Kirilov Consulting"
          />
        </div>
      </div>

      <div class="row text-center content d-flex justify-content-center">
        <div class="col-12 col-md-6 mb-5 pb-5">
          <h1 class="text-white display-1 ml-3 mt-4">We support companies who create products that matter.</h1>
          <div class="display-4"><a class="text-white" href="mailto:georgi@kirilovconsult.com">georgi@kirilovconsult.com</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  layout(context) {
    return 'header';
  },
  data() {
    return {
      email: ''
    };
  },
  computed: {
    deadlineDate: () => {
      var deadline = new Date();

      if (deadline.getMonth() == 11) {
        deadline.setYear(deadline.getYear() + 1)
        deadline.setMonth(0)
      } else {
        deadline.setMonth(deadline.getMonth() + 1)
      }
      return deadline.toDateString()
    }
  },
  methods: {
    validateEmail(email) {
      var re = /^(([^<>()[\]\\.,;:\s@\"]+(\.[^<>()[\]\\.,;:\s@\"]+)*)|(\".+\"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    },
    subscribe(e) {
      e.preventDefault();

      if (!this.validateEmail(this.email)) {
        this.$toast.error('Please enter correct email 💥');
        return;
      }

      this.$axios.post('https://formspree.io/mvorogja', {
        _replyto: this.email
      });

      this.$toast.success('Successfully subscribed! 📬');
    }
  }
};
</script>

<style lang="scss">
.content {
  margin-top: 250px;

  @media only screen and (max-width: 1200px) {
    margin-top: 150px;
  }
  @media only screen and (max-width: 768px) {
    margin-top: 70px;
  }
}
.logo {
  width: 100px;
}
.logo-text {
  max-width: 250px;
}
.navbar {
  background-color: transparent;
}
.size1 {
  width: 100%;
  min-height: 100vh;
}
.overlay1 {
  position: relative;
  z-index: 1;
}

.overlay1::before {
  content: '';
  display: block;
  position: absolute;
  z-index: -1;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background: #30bab6;
  // background: -webkit-linear-gradient(top, #009efd, #2af598);
  // background: -o-linear-gradient(top, #009efd, #2af598);
  // background: -moz-linear-gradient(top, #009efd, #2af598);
  // background: linear-gradient(to bottom, #009efd, #2af598);
  background: linear-gradient(180deg, #11cdef 0, #1171ef 100%);
  opacity: 0.8;
}

.bg-img1 {
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}

.flip-card__top,
.flip-card__bottom,
.flip-card__back-bottom,
.flip-card__back::before,
.flip-card__back::after {
  color: white !important;
}
.flip-card__top-4digits,
.flip-card__bottom-4digits,
.flip-card__back-bottom-4digits,
.flip-card__back-4digits::before,
.flip-card__back-4digits::after {
  color: white !important;
}
.flip-card__bottom,
.flip-card__back-bottom,
.flip-card__bottom-4digits,
.flip-card__back-bottom-4digits {
  color: white !important;
}

.flip-clock__slot {
  color: rgb(68, 43, 43) !important;
}

.__nuxt-error-page {
  padding: 1rem;
  background: #f7f8fb;
  color: #47494e;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;

  font-weight: 100 !important;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -webkit-font-smoothing: antialiased;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}
.__nuxt-error-page .error {
  max-width: 450px;
}
.__nuxt-error-page .title {
  font-size: 1.5rem;
  margin-top: 15px;
  color: #47494e;
  margin-bottom: 8px;
}
.__nuxt-error-page .description {
  color: #7f828b;
  line-height: 21px;
  margin-bottom: 10px;
}
.__nuxt-error-page a {
  color: #7f828b !important;
  text-decoration: none;
}
.__nuxt-error-page .logo {
  position: fixed;
  left: 12px;
  bottom: 12px;
}
</style>