<template>
  <div class="container">
    <h3 class="pb-3">İlan Detayları</h3>
    <table class="table table-striped table-bordered">
      <tr>
        <th scope="col">Pozisyon İsmi:</th>
        <td>{{ detailedJob.positionName }}</td>
      </tr>
      <tr>
        <th scope="col">Şirket:</th>
        <td>{{ detailedJob.companyName }}</td>
      </tr>
      <tr>
        <th scope="col">İlan Süresi:</th>
        <td>{{ detailedJob.durationDay }}</td>
      </tr>
      <tr>
        <th scope="col">Ülke:</th>
        <td>{{ detailedJob.countryName }}</td>
      </tr>
      <tr>
        <th scope="col">Şehir:</th>
        <td>{{ detailedJob.cityName }}</td>
      </tr>
      <tr>
        <th scope="col">İlçe:</th>
        <td>{{ detailedJob.townName }}</td>
      </tr>
      <tr>
        <th scope="col">Adres:</th>
        <td>{{ detailedJob.address }}</td>
      </tr>
      <tr>
        <th scope="col">Posta Kodu:</th>
        <td>{{ detailedJob.postalCode }}</td>
      </tr>
      <tr>
        <th scope="col">Açıklama:</th>
        <td>{{ detailedJob.description }}</td>
      </tr>
      <tr></tr>
      <tr>
        <th scope="col">Telefon Numarası:</th>
        <td>{{ contactPhone }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "JobDetail",
  components: {},
  data() {
    return {
      detailedJobs: [],
    };
  },
  computed: {
    detailedJob() {
      return this.detailedJobs.find((job) => job.id === this.$route.params.id);
    },
    contactPhone() {
      return (
        this.detailedJob.contactPhone.countryCallingCode +
        this.detailedJob.contactPhone.areaCode +
        this.detailedJob.contactPhone.number
      );
    },
  },

  created() {
    fetch("http://localhost:3000/jobDetail")
      .then((response) => {
        return response.json();
      })
      .then((data) => {
        this.detailedJobs = data;
      });
  },
};
</script>
