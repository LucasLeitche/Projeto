<template>
    <div>
        <div class="container">
            <div class="d-flex flex-direction-column">
                <h4>Quais adesivos:</h4>
                <div>
                    <input type="checkbox" value="React" v-model="pedido.items" ><span> React </span>
                </div>
                <div style="margin-top:5px">
                    <input type="checkbox" value="Vue" v-model="pedido.items"><span> Vue </span>
                </div>
                <div style="margin-top:5px">
                    <input type="checkbox" value="Angular" v-model="pedido.items"> <span> Angular </span>
                </div>
            </div>
            <div class="d-flex flex-direction-column">
                <h4>Quantos adesivos de cada?</h4>
                <div class="d-flex align-items-center">
                    <button class="btn btn-plus" :class="pedido.quantidade <=0 ? 'disabled' : ''" @click="pedido.quantidade--" :disabled="pedido.quantidade <=0"><span>-</span></button>
                    <input class="input-form" v-model.number="pedido.quantidade" style="margin: 0 2px 0 2px" type="number">
                    <button class="btn btn-plus" @click="pedido.quantidade++">+</button>
                </div>
            </div>
            <div class="d-flex flex-direction-column">
                <h4>Observações:</h4>
            <textarea v-model="pedido.observacao" cols="30" rows="10"></textarea>
            </div>
        </div>
            <div style="background:#e5e5e5" class="footer ">
                <button class="btn" @click="handleEmitSale">Enviar</button>
            </div>
    </div>
</template>

<script>
export default {
    props:{
        pedido:{
            type: Object
        }
    },
    methods:{
        handleEmitSale(){
            this.$emit('pagamento')
        }
    }
}
</script>

<style>
.footer{
    margin-top: 40px;
    display: flex;
    justify-content: end;
    padding: 30px 40px !important;
}
</style>