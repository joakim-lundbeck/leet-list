<template>
    <div>
        Sort on:
        <button
            @click="changeNameSortOrder()"
            type="button"
            class="btn btn-link">
            Name
            <i v-show="sortingName === 1" class="'bi bi-sort-alpha-down"></i>
            <i v-show="sortingName === 2" class="'bi bi-sort-alpha-up"></i>
        </button>

        <button
            @click="changeOfficeSortOrder()"
            type="button"
            class="btn btn-link">
            Office
            <i v-show="sortingOffice === 1" class="'bi bi-sort-alpha-down"></i>
            <i v-show="sortingOffice === 2" class="'bi bi-sort-alpha-up"></i>
        </button>
    </div>
</template>

<script>
export default {
    name: 'Sorting',
    props: [ 
        'sortingName', 
        'sortingOffice' 
    ],

    data() {
        return {
            name: 0,
            office: 0
        }
    },

    methods: {
        changeNameSortOrder() {
            this.name = this.sortingName === 2 ? 0 : this.sortingName + 1
            this.$emit('update:sortingName', this.name)
        },

        changeOfficeSortOrder() {
            this.office = this.sortingOffice === 2 ? 0 : this.sortingOffice + 1
            this.$emit('update:sortingOffice', this.office)
        }
    }
}
</script>