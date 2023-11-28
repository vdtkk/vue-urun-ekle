<template>
        <div class="row product-container">
        <app-product v-for="product in productList">

            
           <div class=""> <img class="card-img-top" style=" " :src="product.selectedImage" :alt="product.title"></div> 
                        <div class="card-body">
                            <h5 class="card-title">{{product.title}}</h5>
                            <small>
                                <strong>Adet : </strong> {{product.count}} </small>
                            <br>
                            <small>
                                <strong>Fiyat : </strong> {{ product.price }}  </small>
                            <br>
                            <small>
                                <strong>Tutar : </strong>{{ product.totalPrice }} </small>
                        </div>

        </app-product>

        </div>
</template>
<script>
    import { eventBus } from "../main";
    import Product from "./Product.vue"

export default{
 

    components: {

        appProduct:Product

    },
    data(){

        return{

            productList: [],
        }
    },
    created(){
        //eventBus child'den childe taşınmadıında kullanılır. 
        
        eventBus.$on("productAdded",(product)=>{
            this.productList.push(product);

        });

    }

  }

 
</script>
