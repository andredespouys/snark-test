<template>
  <div class="ex-3">
    <h2 class="ex-title">3- Security Checks</h2>
    <SecurityList :data="organisation" :nb-months="3"></SecurityList>
  </div>
</template>

<script>
import SecurityList from "./SecurityList.vue";

export default {
  components: {
    SecurityList,
  },
  data() {
    return {
      organisation : {
        name: "entreprise",
        securityCheck: "03/10/2021",
        services: [
          {
            name: "commercial",
            securityCheck: "03/10/2021",
            services: [
              {
                name: "vente",
                securityCheck: "14/11/2021"
              },
              {
                name: "marketing",
                securityCheck: "30/06/2020"
              },
              {
                name: "communication",
                securityCheck: "08/03/2021",
                services: [
                  {
                    name: "design",
                    securityCheck: "27/07/2021"
                  }
                ]
              }
            ]
          },
        {
          name: "technique",
          securityCheck: "24/08/2021",
          services: [
            {
              name: "electronique",
              securityCheck: "14/11/2021"
            },
            {
              name: "robotique",
              securityCheck: "30/06/2020",
              services: [
                {
                  name: "mécanique",
                  securityCheck: "12/08/2021"
                },
                {
                  name: "automatisme",
                  securityCheck: "01/09/2021"
                },
                {
                  name: "IA",
                  securityCheck: "07/09/2021"
                }
              ]
            }
          ]
        },
        {
          name: "logistique",
          securityCheck: "03/10/2021",
          services: [
            {
              name: "transport",
              securityCheck: "14/11/2021"
            },
            {
              name: "etiquetage",
              securityCheck: "30/06/2020"
            },
            {
              name: "nettoyage",
              securityCheck: "05/09/2021"
            }
          ]
        }
      ]
      },
    };
  },
};
</script>
<style>
.ex-3{
  display: flex;
  flex-direction: column;
  align-items: center;
}
.ex-title{
  font-size: 2rem;
  font-weight: 500;
}
</style>
