<script setup lang="ts">

    import { reactive, computed } from 'vue';

    const cart = reactive({
        category: 'hosting',
        description: 'Carrito de compras de Joan',
        currency: 'USD',
        items: [
            {
                id: 1,
                name: 'basic',
                price: 20,
            },
            {
                id: 2,
                name: 'medium',
                price: 30,
            },
            {
                id: 3,
                name: 'pro',
                price: 40,
            }
        ]
    })

    const msg = computed({
        get(){
            return cart.description;
        },
        set(newValue){
            cart.description = newValue;
        }
    });

    const totalPrice = computed( () => {
        return cart.items.reduce((accumulator, current) => accumulator + current.price, 0);
    });

    const quantity = computed( () => {
        return cart.items.length;
    });

</script>

<template>
    <div>
        Mensaje: {{ msg }}
        <br>
        Precio: {{ totalPrice }}
    </div>
    <br>
    <div>
        Elementos del carrito:
        {{ quantity }}
    </div>
    <br>
    <input type="text" v-model="msg">

    <br><br><br>

</template>

<style scoped>
    input{
        width: 300px;
        height: 30px;
    }
</style>