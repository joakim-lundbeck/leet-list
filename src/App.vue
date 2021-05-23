<template>
  <div id="app" class="container">
    <h1>The fellowship of the Tretton37</h1>
  </div>
</template>

<script>


export default {
  name: 'Leet-List',
  
  data () {
    return {
      enabledEmployees: []  
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
