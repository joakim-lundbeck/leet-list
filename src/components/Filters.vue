<template>
    <div class="card-body">
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
</template>

<script>

export default {
    props: [ 'nameFilter' ],

    data() {
        return {
        filter: ''
        }
    },
}

</script>
