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

        </div>
    </div>
</template>

<script>
export default {
  name: 'EmployeeCard',
  props: [ 'employee' ],

  computed: {
      profilePicture() {
          return this.employee.imagePortraitUrl ?? './img/placeholder.jpeg'
      }
  }
}
</script>