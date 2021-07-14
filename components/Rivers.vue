<template>
  <div>
    <div v-if="loading" class="loading">
      <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" style="margin: auto; display: block; shape-rendering: auto;" width="200px" height="200px" viewBox="0 0 100 100" preserveAspectRatio="xMidYMid">
        <circle cx="50" cy="50" fill="none" stroke="#158876" stroke-width="10" r="35" stroke-dasharray="164.93361431346415 56.97787143782138">
          <animateTransform attributeName="transform" type="rotate" repeatCount="indefinite" dur="1s" values="0 50 50;360 50 50" keyTimes="0;1"></animateTransform>
        </circle>
      </svg>
    </div>
    <div class="rivers">
      <div class="card" v-for="river in rivers" :key="river.id">
        <img class="card-img" :src="river.image" alt="preview" />
        <div class="card-body">
          <h3 class="card-title">{{ river.title }}</h3>
          <p class="card-subtitle">{{river.length}}</p>
          <div class="card-tags">
            <span v-for="country in river.countries" :key="country">
              {{ country }}
            </span>
          </div>
          <article class="card-description">
            <p>{{ river.description }}</p>
          </article>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'rivers',
  data() {
    return {
      rivers: [],
      loading: true,
    };
  },
  async fetch() {
    this.rivers = await fetch('https://api.nuxtjs.dev/rivers')
    .then(res =>
      res.json()
    )
    this.rivers.sort(
      (a, b) =>
        a.length.split(' ')[0].replace(',', '') -
        b.length.split(' ')[0].replace(',', '')
    )
    this.loading = false;
  },
};
</script>

