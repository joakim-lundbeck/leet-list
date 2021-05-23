<template>
    <div>
        <div class="row" v-if="numberOfPages > 1">
            <div class="col-12">
                <ul class="pagination">
                
                    <li 
                        :class="['page-item', index == selectedPage ? 'active' : '' ]" 
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
            </div>
        </div>
    </div>
</template>

<script>
export default  {
    props: [ 
        'numberOfPages', 
        'selectedPage' 
    ]
}
</script>
