<template>
  <div id="app">
    <company
      v-for="element of elements"
      :logo="element.logo"
      :company_name="element.company_name"
      :email="element.email"
      :title="element.title_"
      :rating="element.rating"
      :screenShot="element.screenshot"
      :twitterUrl="element.twitterUrl"
      :linkedInUrl="element.linkedinUrl"
      :facebookUrl="element.facebookUrl"
      :specialities="element.specialties"
      :companyAddress="element.companyAddress"
      :Short_description="element.Short_description"
      :Long_description="element.Long_description"
      :website="element.website_"
    ></company>
  </div>
</template>

<style lang="scss">
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  font-family: "Roboto", sans-serif;
  font-size: 10px;
}

img {
  width: 100%;
}

body {
  width: 100%;
  display: flex;
  justify-content: center;
  background-color: #eee;
  padding: 0;
}
</style>

<script>
import axios from "axios";
import company from "./components/company";
export default {
  data: function() {
    return {
      elements: []
    };
  },

  components: {
    company: company
  },

  methods: {
    async getData() {
      this.elements = await axios
        .get("http://localhost:8080/front-end_data.json")
        .then(response => {
          return response.data;
        });
      console.log(this.elements);
    }
  },

  mounted() {
    this.getData();
  }
};
</script>