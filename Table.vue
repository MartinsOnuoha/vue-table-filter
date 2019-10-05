<template>
  <div class="container">
    <div>
      <h2 class="header">Vue JS Table</h2>
      <div class="search-bar">
        <input v-model="search" type="text" class="search" />
      </div>
    </div>
    <table>
      <thead>
        <tr>
          <th>Name</th>
          <th>Email</th>
          <th>Job Title</th>
          <th>Age</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(user, i) in users" :key=i>
          <td data-column="First Name">{{ user.name }}</td>
          <td data-column="Last Name">{{ user.email }}</td>
          <td data-column="Job Title">Chief Sandwich Eater</td>
          <td data-column="Twitter">{{ user.age }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style lang="css">
.container {
  margin: 5rem;
  text-align: center;
}
table {
  width: 750px;
  border-collapse: collapse;
  margin: 50px auto;
}

/* Zebra striping */
tr:nth-of-type(odd) {
  background: #eee;
}

th {
  background: #3498db;
  color: white;
  font-weight: bold;
}

td,
th {
  padding: 10px;
  border: 1px solid #ccc;
  text-align: left;
  font-size: 18px;
}

.search {
  border-radius: 10px;
  border: 1px solid #ccc;
  padding: 0.4rem;
  width: 30%;
  height: 20px;
}
.search:focus { outline: none }
</style>

<script>
import dataStore from "./datastore";

export default {
  name: "vue-table",
  data() {
    return {
      users: dataStore,
      search: ''
    };
  },
  watch: {
    search (query) {
      this.users = dataStore
      this.users = this.users.filter(x => x.name.includes(query) || x.email.includes(query))
    },
  },
  mounted() {
  }
};
</script>
