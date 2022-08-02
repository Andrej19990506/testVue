<template>
    <div class="App">
        <FormProduct @create="createProduct" />
        <CardsProdust @create="createProduct" :products='products' @remove='setClose' />
    </div>
</template>

<script>
import FormProduct from './components/FormProduct.vue'
import CardsProdust from './components/CardsProdust.vue'

export default {
    components:{
    FormProduct,
    CardsProdust
},
    data() {
        return {
                products:[
                ],
        }
    },
    methods: {
        createProduct(product){
            this.products.push(product)
            this.saveProducts();
        },
        setClose(product){
            this.products = this.products.filter(c => c.id !== product.id)
            console.log(product.id);
            this.saveProducts(product);
        },
        saveProducts() {
            const parsed = JSON.stringify(this.products);
            localStorage.setItem('products', parsed);
        }
    },
    mounted() {
        if (localStorage.getItem('products')) {
            this.products = JSON.parse(localStorage.products);
            try {
                this.products = JSON.parse(localStorage.getItem('products'));
            } catch (e) {
                localStorage.removeItem('products');
            }
        }

    },
}
</script>

<style lang="scss">






@import './assets/style.scss';
*{
    margin: 0;
    padding: 0;
}


.App{
    display: flex;
    height: 100vh;
}


</style>