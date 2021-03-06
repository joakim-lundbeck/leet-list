<template>
  <div id="app" class="container">
    <h1>The fellowship of the Tretton37</h1>

    <div class="row">
      <div class="col-12">
        <div class="card mb-2">
          <Filters 
            :nameFilter.sync="nameFilter"
            :offices.sync="offices"
          />
        </div>
      </div>
    </div>

    <div class="row">
      <div class="col-12">
        <Sorting
          :sortingName.sync="sortingName"
          :sortingOffice.sync="sortingOffice" />
      </div>
    </div>
    
    <Pagination
      :numberOfPages="numberOfPages"
      :selectedPage.sync="selectedPage" />

    <div class="row">
      <div v-for="employee in chunkEmployees" :key="employee.email" class="col-3">
        <EmployeeCard :employee="employee" />
      </div>
    </div>

    <Pagination
      :numberOfPages="numberOfPages"
      :selectedPage.sync="selectedPage" />

  </div>
</template>

<script>
import EmployeeCard from './components/EmployeeCard.vue'
import Filters from './components/Filters.vue'
import Sorting from './components/Sorting.vue'
import Pagination from './components/Pagination.vue'

export default {
  name: 'Leet-List',
  
  components: {
    EmployeeCard,
    Filters,
    Sorting,
    Pagination
  },

  data () {
    return {
      enabledEmployees: [],
      nameFilter: '',
      offices: [],
      sortingName: 0,
      sortingOffice: 0,
      selectedPage: 1
    }
  },

  computed: {
    filteredEmployees() {
      return this.enabledEmployees.filter(employee => {
        return employee.name.toUpperCase().indexOf(this.nameFilter.toUpperCase()) > -1 &&
        this.selectedOffices.includes(employee.office)
      }).map((e, index) => {
          return {
            page: Math.floor(index  / 8) + 1,
            name: e.name,
            office: e.office,
            imagePortraitUrl: e.imagePortraitUrl,
            twitter: e.twitter,
            linkedIn: e.linkedIn,
            gitHub: e.gitHub
          }
      })
    },

    selectedOffices() {
      return this.offices.filter(o => o.selected).map(o => o.name)
    },

    chunkEmployees() {
      return this.filteredEmployees.filter(e => e.page == this.selectedPage)
    },

    numberOfPages() {
      return Math.floor(this.filteredEmployees.length  / 8) + 1
    },
  },

  watch: {
    sortingName() {
      if(this.sortingName === 0) return

      this.chunkEmployees.sort(
        this.sortingName === 1 ? 
          (a, b) => (a.name > b.name) ? 1 : -1 :
          (a, b) => (a.name < b.name) ? 1 : -1
      )
    },

    sortingOffice() {
      if(this.sortingOffice === 0) return

      this.chunkEmployees.sort(
        this.sortingOffice === 1 ? 
          (a, b) => (a.office > b.office) ? 1 : -1 :
          (a, b) => (a.office < b.office) ? 1 : -1
      )
    },

    filteredEmployees() {
      this.selectedPage = 1
    }
  },

  mounted () {
    const axios = require('axios')

    axios
      .get('https://api.1337co.de/v3/employees', {
        headers: {
          'Authorization': 'api-key 14:2021-05-18:lucas.stenberg@tretton37.com 5022ab727cb0cb271ff3a7f59b15cedd7c4c63a47c833668d4dde6adedc557f0'
        }
      }
    )
    .then(
      response => {
        this.enabledEmployees = response.data.filter(e => e.published)

        const uniqueOffices = [...new Set(
          this.enabledEmployees.map(e => e.office)
        )].filter(Boolean).sort()

        this.offices = uniqueOffices.map(e => {
          return {
            name: e,
            selected: true
          }
        })
      }
    )
  }

}
</script>
