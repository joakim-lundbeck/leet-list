<template>
    <div class="card-body">
        <div class="row">
            <div class="col-xl-3 col-sm-12">

                <div class="input-group">

                    <input 
                        type="text" 
                        class="form-control" 
                        placeholder="Name Search" 
                        v-model="filter"
                        @keyup="$emit('update:nameFilter', filter)" >

                    <button
                        v-if="filter.length > 0" 
                        class="btn btn-outline-secondary" 
                        type="button"
                        @click="$emit('update:nameFilter', ''), filter=''">

                    <i class="bi bi-x-circle"></i>

                    </button>
                </div>
            </div>

            <div class="col-xl-9 col-sm-12 mt-sm-2 mt-xl-0">
                <span v-for="office in offices" :key="office.name">

                    <button
                        @click="toggleOffice(office)" 
                        type="button"
                        :class="['btn', office.selected ? 'btn-dark' : 'btn-outline-dark', 'me-2']">
                        
                        <span class="d-none d-lg-inline">
                            <i :class="['bi', office.selected ? 'bi-check-circle' : 'bi-circle']"></i>
                        </span>
                        {{office.name}}
                    </button>

                </span>
            </div>
        
        </div>
        
    </div>
</template>

<script>

export default {
    name: 'Filters',
    props: [ 
        'nameFilter', 
        'offices' 
    ],

    data() {
        return {
            filter: ''
        }
    },

    methods: {
        toggleOffice(office) {
            const officeIndex = this.offices.findIndex(o => o.name === office.name)
            this.offices[officeIndex].selected = !office.selected
            this.$emit('update:offices', this.offices)
        }
    }
}

</script>
