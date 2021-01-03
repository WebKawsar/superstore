<template>
    <div>
        <Header @search="search"></Header>

        <div class="container">
            <div class="row">
                <div class="col-md-9">
                    <Card @newItemAdded="addToCart" :items="items"></Card>
                </div>
                <div class="col-md-3">
                    <Cart @removeItem="removeCart" :items="cart"></Cart>
                </div>
            </div>
        </div>

        
        
    </div>
</template>

<script>
import Header from "../Header/Header";
import Card from "../Card/Card";
import Cart from "../Cart/Cart";
import FakeData from "../FakeData/FakeData";

    export default {
        components: {
            Header,
            Card,
            Cart
        },
        data(){
            return {
               items: [],
               cart: []
            }
        },
        methods: {
            addToCart(item){
                this.cart.push(item);
            },
            removeCart(index){
                this.cart.splice(index, 1)
            },
            search(keyword){
                this.items = FakeData.filter(item => {
                    return item.title.toLowerCase().indexOf(keyword.trim().toLowerCase()) !== -1 
                })
            }
        },
        mounted(){

            this.items = FakeData;
        }
    }
</script>

<style scoped>

</style>