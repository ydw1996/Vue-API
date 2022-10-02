<template>
  <HeaderCont />
  <TitleCont name1="About" name2="Api" />
  <section className="about__cont">
    <div className="container">
      <div className="about__inner">
        <div className="about" v-for="about in abouts" v-bind:key="about.title">
          <div className="about__txt">
            <h3>{{ about.title }}</h3>
            <h3>{{ about.desc }}</h3>
          </div>
          <div className="about__img">
            <img :src="about.img" :alt="about.title" />
          </div>
        </div>
      </div>
    </div>
  </section>
  <ContactCont />
  <FooterCont />
</template>

<script>
import HeaderCont from "@/components/HeaderCont.vue";
import FooterCont from "@/components/FooterCont.vue";
import TitleCont from "@/components/TitleCont.vue";
import ContactCont from "@/components/ContactCont.vue";

export default {
  components: {
    HeaderCont,
    FooterCont,
    TitleCont,
    ContactCont,
  },
  data: function () {
    return {
      abouts: [
        {
          title: "유튜브 API",
          desc: "유튜브에서 제공하는 API를 가져와서 작업했습니다.",
          img: "https://images.unsplash.com/photo-1663326223816-7d8d969eddfc?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2148&q=80",
        },
        {
          title: "TMDB API",
          desc: "TMDB에서 제공하는 API를 가져와서 작업했습니다.",
          img: "https://images.unsplash.com/photo-1661956602868-6ae368943878?ixlib=rb-1.2.1&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2370&q=80",
        },
        {
          title: "Unsplash API",
          desc: "Unsplash에서 제공하는 API를 가져와서 작업했습니다.",
          img: "https://images.unsplash.com/photo-1663431905837-09cf339461ce?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2807&q=80",
        },
      ],
    };
  },
};
</script>

<style scoped lang="scss">
.about__cont {
  background-color: var(--black);
}

.about__inner {
  .about {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    padding-bottom: 30vh;
    color: var(--white);
    font-family: var(--kor_font);

    .about__img {
      flex: 0 0 64%;
    }

    .about__txt {
      flex: 0 0 32%;
      text-align: justify;

      h3 {
        margin-bottom: 30px;
        font-size: 1.4rem;
        line-height: 1;
      }

      p {
        font-size: 1rem;
        line-height: 1.6;
      }
    }

    &:nth-child(even) {
      flex-direction: row-reverse;
    }
  }
}
</style>
