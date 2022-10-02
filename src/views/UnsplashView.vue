<template>
  <HeaderCont />
  <TitleCont name1="Unsplash" name2="Api" />
  <div class="image__cont">
    <div class="container">
      <div class="image__search">
        <form @submit.prevent="SearchImages()">
          <div>
            <label for="search"></label>
            <input
              type="search"
              id="search"
              placeholder="검색하기"
              v-model="search"
            />
            <button type="submit">검색</button>
          </div>
        </form>
      </div>
      <div class="image__list">
        <ul>
          <li v-for="image in images" :key="image.id">
            <a :href="`https://unsplash.com/photos/${image.id}`">
              <img :src="image.urls.regular" :alt="image.id" />
            </a>
          </li>
        </ul>
      </div>
    </div>
  </div>
  <ContactCont />
  <FooterCont />
</template>

<script>
import HeaderCont from "@/components/HeaderCont.vue";
import FooterCont from "@/components/FooterCont.vue";
import TitleCont from "@/components/TitleCont.vue";
import ContactCont from "@/components/ContactCont.vue";
import { ref } from "vue";

export default {
  components: {
    HeaderCont,
    FooterCont,
    TitleCont,
    ContactCont,
  },
  setup() {
    const images = ref([]);
    const search = ref("ocean");
    const SearchImages = () => {
      fetch(
        `https://api.unsplash.com/search/photos?query=${search.value}&client_id=jGbDbr4a56tzr3H7rOKt8zDwnzQ6Dv8eID5gzzL8t0s&per_page=30`
      )
        .then((response) => response.json())
        .then((data) => {
          images.value = data.results;
          search.value = "";
          console.log(images);
        })
        .catch((error) => console.log("error", error));
    };
    SearchImages();
    return {
      images,
      search,
      SearchImages,
    };
  },
};
</script>

<style scoped lang="scss">
.image__cont {
  background-color: var(--black);
}
.image__list ul {
  width: 100%;
  display: flex;
  flex-wrap: wrap;

  li {
    flex: 1 1 20%;
    margin: 1%;
    overflow: hidden;
    border-radius: 0.4em;

    span {
      -webkit-line-clamp: 2;
      -webkit-box-orient: vertical;
      color: #fff;
      color: var(--white);
      display: -webkit-box;
      font-family: SCoreDream;
      font-family: var(--subKor_font);
      overflow: hidden;
      padding-top: 10px;
      text-overflow: ellipsis;
    }
  }
}

.image__list ul img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: all 0.1s;
}

.image__list li img {
  transition: all 0.5s;
}
.image__list li:hover img {
  transform: scale(1.05);
}

.image__search {
  background: var(--black);

  .container {
    position: relative;
  }

  h2 {
    color: var(--white);
    font-size: 40px;
    height: 0;
    text-indent: -9999px;
    width: 0;
  }

  input {
    background: var(--black);
    border: 2px solid var(--light_border);
    border-radius: 50px;
    color: #f0eeeb;
    color: var(--white);
    margin: 0 1% 5%;
    padding: 1rem 3rem 1rem 2rem;
    width: 98%;
  }
  button {
    background: #fff;
    border: 0;
    border-radius: 50%;
    color: var(—black);
    font-family: var(—subKor_font);
    font-size: 12px;
    height: 40px;
    position: absolute;
    right: 22px;
    top: 9px;
    transition: opacity 0.3s ease;
    width: 40px;
  }
}
</style>
