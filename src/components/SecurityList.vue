<template>
  <div class="list">
    <h3 style="font-size: 1.5rem;">Number Of months:{{ nbMonths }}</h3>
    <ul>
      <li v-for="serviceName in result" :key="serviceName">
        {{ serviceName }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    data: {
      type: Object,
      required: true,
    },
    nbMonths: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      result: [],
    };
  },
  methods: {
    checkSecurity(service, lastSecurityCheckDate) {
      const currentDate = new Date();
      const lastCheckDate = new Date(lastSecurityCheckDate);
      const diffMonths =
        (currentDate.getFullYear() - lastCheckDate.getFullYear()) * 12 +
        (currentDate.getMonth() - lastCheckDate.getMonth());

      if (diffMonths > this.nbMonths && !this.result.includes(service.name)) {
        this.result.push(service.name);
      }

      if (service.services) {
        service.services.forEach((subService) => {
          this.checkSecurity(
            subService,
            subService.securityCheck || lastSecurityCheckDate
          );
        });
      }
    },
  },
  created() {
    this.checkSecurity(this.data, this.data.securityCheck);
  },
};
</script>

<style>
.list{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
ul {
  display: flex;
  list-style: none;
  padding: 1rem;

}

li {
  margin: 5px;
  display: flex;
  align-items: center;
}

.service-name {
  font-weight: bold;
}

.months {
  margin-left: 10px;
  color: #888;
}
</style>
