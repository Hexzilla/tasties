<template>
  <div id="home">
    <div class="home-bg bg-small-pc">
      <img src="@/assets/images/bg-small-pc.png" />
    </div>
    <div class="home-bg bg-pc">
      <img src="@/assets/images/bg-pc.png" />
    </div>
    <div class="home-bg bg-mobile">
      <img src="@/assets/images/bg-mobile.png" />
    </div>
    <div class="home-bg bg-wide">
      <img src="@/assets/images/bg-wide.png" />
    </div>
    <MainNav />
    <div class="nav-logo">
      <img
        data-aos="fade-down"
        src="@/assets/images/nav/nav-logo.svg"
        alt="Tasties Logo"
      />
    </div>
    <div class="info-btn-wrap">
      <a>Coming soon</a>
    </div>

    <header>
      <div class="content" id="staking">
        <div class="header-img-wrap" data-aos="fade-up">
          <img
            class="pc"
            src="@/assets/images/staking/staking-header-img.svg"
            alt="Header image"
          />
          <img
            class="mobile"
            src="@/assets/images/staking/staking-header-mobile.svg"
            alt="Header image"
          />
        </div>
        <p class="stake-text" data-aos="fade-up">
          Staking is a major part of the Tasties Ecosystem. With our $treat
          token, you will be able to earn, collect, and spend $treat throughout
          Sweetland. With our growing community the possibilities for our token
          are endless.
        </p>
        <div class="boxes-wrap">
          <div class="box-wrap" data-aos="fade-right">
            <div class="img-wrap">
              <img
                src="@/assets/images/staking/stake-box.svg"
                alt="Wooden box"
              />
            </div>
            <p>
              Staking your Tasties opens many possibilities! Put your Tasties to
              work in The Factory to earn $treat token! Every Tasty earns at
              least 10 $treat per day by being staked, however rarer tastes will
              earn you more!
            </p>
          </div>
          <div class="box-wrap" data-aos="fade-up">
            <div class="img-wrap">
              <img
                src="@/assets/images/staking/earn-box.svg"
                alt="Wooden box"
              />
            </div>
            <p>
              Keep your Tasties staked in the factory to earn a passive amount
              of $treat token every day! The more tasties you have staked the
              more you will earn. Make sure to check on the factory every day to
              see how much your tasties have earned and collect your rewards!
            </p>
          </div>
          <div class="box-wrap" data-aos="fade-left">
            <div class="img-wrap">
              <img
                src="@/assets/images/staking/spend-box.svg"
                alt="Wooden box"
              />
            </div>
            <p>
              With each Tastie earning you at least 10 $treat token per day, you
              can now put this to use in the Tasties ecosystem, which offers
              many ways to spend your $treat token! Once you have earned your
              $treat you can now use this in the Tasty Shop.
            </p>
          </div>
        </div>
      </div>
    </header>
    <section class="rarities" id="rarities" data-aos="fade-up">
      <div class="rarities-img-wrap">
        <img class="pc" src="@/assets/images/rarities-img.png" alt="Rarities" />
        <img
          class="mobile"
          src="@/assets/images/rarities-img-mobile.png"
          alt="Rarities"
        />
      </div>
    </section>
    <section class="faq" id="faq" data-aos="fade-up">
      <div class="faq-header-wrap">
        <img src="@/assets/images/faq/faq-header.svg" alt="Faq header" />
      </div>
      <div class="content">
        <!-- <div class="img-wrap" data-aos="fade-right">
          <img src="@/assets/images/faq/faq-stand.svg" alt="Stand" />
        </div> -->
        <div class="faqs">
          <div class="faq-item" data-aos="fade-left" @click="toggleFaq">
            <div class="question">What is the total supply?</div>
            <div class="answer">5,000</div>
          </div>
          <div class="faq-item" data-aos="fade-left" @click="toggleFaq">
            <div class="question">When will Tasties launch?</div>
            <div class="answer">TBA</div>
          </div>
          <div class="faq-item" data-aos="fade-left" @click="toggleFaq">
            <div class="question">What is the price of minting?</div>
            <div class="answer">Completely Free!</div>
          </div>
          <div class="faq-item" data-aos="fade-left" @click="toggleFaq">
            <div class="question">How many Tasties can I mint?</div>
            <div class="answer">1 per wallet</div>
          </div>
          <div class="faq-item" data-aos="fade-left" @click="toggleFaq">
            <div class="question">Can I ask my own question?</div>
            <div class="answer">
              Yes! Go to our support questions part of our discord.
            </div>
          </div>
        </div>
      </div>
    </section>
    <footer>
      <div class="footer-bg-wrap">
        <img src="@/assets/images/bg-footer.svg" />
      </div>
      <div class="content">
        <div class="logo-wrap">
          <img src="@/assets/images/footer/logo.svg" alt="Logo" />
        </div>
        <div class="socials-wrap">
          <a href="https://twitter.com/tastiesnft">
            <img src="@/assets/images/general/twitter.svg" alt="Twitter" />
          </a>
          <a href="">
            <img src="@/assets/images/general/instagram.svg" alt="Instagram" />
          </a>
          <a href="https://t.co/Bwn2XTRe9m">
            <img src="@/assets/images/general/discord.svg" alt="Discord" />
          </a>
        </div>
        <div class="copy">© 2022 TASTIES</div>
      </div>
    </footer>
  </div>
</template>

<script>
import AOS from "aos";
import "aos/dist/aos.css";
import { mapState } from "vuex";
import MainNav from "../components/MainNav.vue";

export default {
  components: {
    MainNav,
  },
  name: "HomeView",
  computed: {
    ...mapState({
      wallet: (state) => state.Web3.account,
    }),
  },
  async mounted() {
    AOS.init({ once: true, duration: 1000 });
    window.addEventListener("load", AOS.refresh);
    // window.addEventListener("scroll", this.handleScroll);
  },
  unmounted() {
    // window.removeEventListener("scroll", this.handleScroll);
  },
  methods: {
    handleScroll() {
      // this.menuBg = window.scrollY > 100;
    },
    toggleFaq($event) {
      $event.target.classList.toggle("show");
      Array.from(document.querySelectorAll(".faq-item.show")).forEach((el) => {
        if (el === $event.target) {
          return;
        }
        el.classList.remove("show");
      });
    },
    async connectWallet() {
      await this.$store.dispatch("getWeb3Data");
    },
    async comingSoon() {
      this.$store.commit("SET_LOADING_OVERLAY", true);
    },
  },
};
</script>
