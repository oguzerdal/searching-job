<template>
  <div class="container">
    <div class="form-group row">
      <label for="searchInput" class="col-sm-2 col-form-label font-weight-bold"
        >İlan Ara:</label
      >
      <div class="col-sm-4">
        <input
          type="text"
          id="searchInput"
          class="form-control"
          placeholder="pozisyon, firma adı, şehir"
          v-model="search"
          v-on:keyup.enter="filteredJobs"
        />
      </div>
    </div>
    <div>
      <table class="table table-striped table-bordered m-3">
        <thead>
          <tr>
            <th scope="col">Posizyon</th>
            <th scope="col">Şirket İsmi</th>
            <th scope="col">Şehir</th>
            <th scope="col">Semt</th>
            <th scope="col">Detaylara Git</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="job in filteredJobs" v-bind:key="job.jobId">
            <td scope="row">{{ job.positionName }}</td>
            <td>{{ job.companyName }}</td>
            <td>{{ job.cityName }}</td>
            <td>{{ job.townName }}</td>
            <td>
              <router-link :to="{ name: 'jobDetail', params: { id: job.id } }"
                >İlan detaylarını görüntüle</router-link>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<script>
export default {
  name: "Home",
  components: {},
  data() {
    return {
      search: "",
      jobList: [],
    };
  },
  methods: {},
  computed: {
    filteredJobs() {
      return this.jobList.filter((job) =>
        Object.values(job)
          .map(String)
          .some((i) => i.toLowerCase().includes(this.search.toLowerCase()))
      );
    },
  },
  created() {
    fetch("http://localhost:3000/jobList")
      .then((response) => {
        return response.json();
      })
      .then((data) => {
        this.jobList = data;
      });
  },
};
</script>
<style></style>
