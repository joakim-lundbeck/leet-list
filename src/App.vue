<template>
  <div id="app" class="container">
    <h1>The fellowship of the Tretton37</h1>

    <div class="row">
      <div class="col-12">
        <div class="card mb-2">
          <Filters :nameFilter.sync="nameFilter"></Filters>
        </div>
      </div>
    </div>

    <div class="row">
      <div v-for="employee in filteredEmployees" :key="employee.email" class="col-3">
        <EmployeeCard :employee="employee"></EmployeeCard>
      </div>
    </div>
  </div>
</template>

<script>
import EmployeeCard from './components/EmployeeCard.vue'
import Filters from './components/Filters.vue'

export default {
  name: 'Leet-List',
  
  components: {
    EmployeeCard,
    Filters
  },

  data () {
    return {
      enabledEmployees: [],
      nameFilter: ''
    }
  },

  computed: {
    filteredEmployees() {
      return this.enabledEmployees.filter(employee => {
        return employee.name.toUpperCase().indexOf(this.nameFilter.toUpperCase()) > -1
      })
    }
  },

  mounted () {
    const axios = require('axios')

    axios
      .get('/mock/employees.json', {
        headers: {
          'Authorization': 'api-key 14:2021-05-18:lucas.stenberg@tretton37.com 5022ab727cb0cb271ff3a7f59b15cedd7c4c63a47c833668d4dde6adedc557f0'
        }
      }
    )
    .then(
      response => {
        this.enabledEmployees = response.data.filter(e => e.published)
      }
    )
  }

}
</script>
