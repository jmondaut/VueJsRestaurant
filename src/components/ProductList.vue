<template>

    <div class="container">
        <div class="row">
        <div v-for="prod in productList" :key="prod.product">
            <div>
            <b-card
                :title="prod.product"
                :img-src="prod.image"
                :img-alt="prod.product"
                img-top
                tag="article"
                style="max-width: 20rem;"
                class="mb-2 mx-2"
            >
                <b-card-text>
                    The popular German sandwich.
                    <hr>
                    <div v-if="prod.stock > 0">
                        There's {{prod.stock}} left in stock.
                        <button @click="addProductToCart(prod.product)" class="btn-primary">Add to cart</button>
                        <p><strong v-show="prod.onSale">On sale!</strong></p>
                    </div>
                    <p v-else>This product is out of stock</p>
                </b-card-text>
            </b-card>
            </div>
        </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ProductList',
    data() {
        return {
            productList: [
            {
                product: "Kebab",
                image: './img/kebab.png',
                stock: 3,
                onSale: true,
            },
            {
                product: "Grec",
                image: './img/kebab.png',
                stock: 0,
                onSale: false
            }
            ]        
        }    
    },
    methods: {
        addProductToCart(productName){
            this.$emit("addProductToCart", productName)
        }
    }
}
</script>

<style scoped>
.product-picture-box{
    border: solid black 2px;
}

.product-picture {
    max-width: 200px;
    max-height: 200px;
    border: solid black 1px;
}
.product-description-box{
    border: solid black 1px;
}

</style>