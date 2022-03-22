<template>
    <div id="principal"  >
        <bar-top-form />
        <etiqueta :pedido="pedido"  @pagamento="handleShowCheckout()" v-if="showEtiqueta"/>
        <pag-form v-if="showCheckoutVenda" :pedido="pedido" :pagamento="pedido.pagamento" @retornar="handleShowPag"/>
    </div>
</template>

<script>
import BarTopForm from './Bar-top-form.vue'
import Etiqueta from './Etiqueta-form.vue'
import PagForm from './PagForm.vue'

export default {
    components:{
        BarTopForm,
        Etiqueta,
        PagForm
    },
    data(){
        return{
            showEtiqueta: false,
            showCheckoutVenda: false,
            pedido: {
                pagamento: {
                    cartao: {showCartao: false, selected: null},
                    debito:{showDebito: false, selected: null},
                    boleto:{showBoleto: false, barcod: 12345678910111213, selected: null},
                    pix:{showPix:false, chavepix: 12345678910111213, selected: null}
                },
                items:[],
                quantidade: 0,
                observacao: null
            }
        }
    },
    methods:{

         handleShowPag(){
            this.showCheckoutVenda = false
            this.showEtiqueta = true
            this.pedido = {}
        },
        handleShowCheckout(){
            this.showEtiqueta = false
            this.showCheckoutVenda = true
            console.log(this.pedido)
        }
    },
    created(){
        this.showEtiqueta = true
    }
}
</script>

<style>
#principal{
    background: #f2f2f2;
    max-width: 70%;
    margin-top: 20px;
    overflow: hidden;
    border: none;
    border-radius: 10px;
}

</style>