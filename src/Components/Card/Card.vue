<template>
    <div>
        <div class="row">
            <div v-for="(item, index) in items" :key="index" class="col-md-4">
                <div class="card" style="width: 18rem;">
                    <img style="height: 180px" :src="item.img" class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">{{item.title}}</h5>
                        <p>$ {{item.price}}</p>
                        <a @click="addToCart(item)" class="btn btn-primary">Add to cart</a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            items: {
                type: Array,
                required: true
            }
        },
        methods: {
            addToCart(item){
                
                this.$emit("newItemAdded", item)
            }
        }
    }
</script>

<style scoped>

</style>