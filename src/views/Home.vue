<template>
  <div class="home">Hello World</div>
</template>

<script>
export default {
  name: "Home",
  components: {},
  data() {
    return {
      loading: true,
      title: 'Global',
      dataDate: '',
      stats: {},
      countries: [],
      loadingImage: require('../assets/motion.gif')
    }
  },
  methods: {
    async fetchCovidData(){
      const res = await fetch('https://api.covid19.com/summary');
      const data = await res.json();
      return data;
    }
  },
  async created(){
    const data = await this.fetchCovidData();
    this.dataDate = data.Date;
    this.stats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  }
};
</script>
