<template>
    <div>
        <div class="row" v-if="numberOfPages > 1">
            <div class="col-12">
                <ul class="pagination">
                
                    <li 
                        :class="['page-item d-none d-xl-inline', index == selectedPage ? 'active' : '' ]" 
                        v-for="index in numberOfPages" 
                        :key="index">

                        <a 
                            @click="$emit('update:selectedPage', index)" 
                            class="page-link" 
                            href="#">
                            {{index}}
                        </a>

                    </li>
                </ul>

                <ul class="pagination d-xl-none">
                    <li :class="['page-item', { disabled: selectedPage === 1 } ]">
                        <a class="page-link" href="#" @click="changePage(-1)">
                            <i class="bi bi-arrow-left"></i> Previous
                        </a>
                    </li>

                    <li :class="['page-item', { disabled: selectedPage === numberOfPages } ]">
                        <a class="page-link" href="#" @click="changePage(1)">
                            Next <i class="bi bi-arrow-right"></i>
                        </a>
                    </li>
                </ul>

                Page: {{selectedPage}} / {{numberOfPages}}
                    
            </div>
        </div>
    </div>
</template>

<script>
export default  {
    props: [ 
        'numberOfPages', 
        'selectedPage' 
    ],

    methods: {
        changePage(page) {
            this.$emit('update:selectedPage', this.selectedPage + page)
        }
    }
}
</script>
