<template>
    <div class="card text-white bg-dark mb-3 me-2">
    
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
  props: [ 'employee' ]
}
</script>