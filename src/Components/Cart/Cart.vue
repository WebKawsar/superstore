<template>
    <div>
        <div v-for="(item, index) in items" :key="index">
            <ul class="list-group">
                <li class="list-group-item d-flex justify-content-between align-items-center"><button @click="removeCart" class="btn btn-danger">-</button>{{item.title}} <span class="badge bg-primary rounded-pill">$ {{item.price}}</span></li>
            </ul>
        </div>
        <div style="margin-top: 20px">
            <ul class="list-group">
                <li class="list-group-item d-flex justify-content-between align-items-center">Total <span class="badge bg-primary rounded-pill">$ {{totalPrice}}</span></li>
            </ul>
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
            removeCart(index){
                this.$emit("removeItem", index)
            }
        },
        computed: {
            totalPrice(){
                let total = 0;
                this.items.forEach(item => {
                    total += parseFloat(item.price)
                })
                return total;
            }
        }
    }
</script>

<style scoped>

</style>