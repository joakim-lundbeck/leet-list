<template>
    <div class="card text-white bg-dark mb-3 me-2">
    
        <img :src="profilePicture" class="card-img-top" :alt="employee.name"> 

        <div class="card-body">
            <div class="row">
                <div class="col-12">
                <h5 class="card-title">{{employee.name}}</h5>
                </div>
            </div>
                            
            <p class="card-text">
                <i class="bi bi-building"></i>
                {{employee.office}}
            </p>

            <div class="col-12">
                <a v-if="employee.linkedIn" :href="'https://www.linkedin.com/' + employee.linkedIn" target="_new"><i class="bi bi-linkedin me-2"></i></a>
                <a v-if="employee.gitHub" :href="'https://github.com/' + employee.gitHub" target="_new"><i class="bi bi-github me-2"></i></a>
                <a v-if="employee.twitter" :href="'https://twitter.com/' + employee.twitter" target="_new"><i class="bi bi-twitter"></i></a>
            </div>

        </div>
    </div>
</template>

<script>
export default {
  name: 'EmployeeCard',
  props: [ 'employee' ],

  computed: {
      profilePicture() {
          return './img/placeholder.jpeg'
      }
  }
}
</script>