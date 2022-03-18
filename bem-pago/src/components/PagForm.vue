<template>
    <div>
        <div class="container">
            <div class="d-flex flex-direction-column">
                <div class="card container-sm" style="padding-bottom:20px!important">
                    <div class="d-flex align-items-center" style="margin-top:20px">
                        <span class="d-flex color-white align-items-center justify-content-center" style="color: #e5e5e5; border: 1px solid transparent; border-radius:50%; width: 30px; height:30px; background: #82cb6f;">
                            1
                        </span>
                        <span style="color: #636363; font-size:22px; margin-left:10px">Forma de Pagamento</span>
                    </div>
                    <div style="margin: 40px 0!important">
                        <small style="color: #636363; ">Selecione uma forma de pagamento abaixo para  <br> finalizar seu pedido</small>
                    </div>
                    <div class="card "  style="margin-top: 5px; padding: 10px 10px;color: #636363; border-bottom: 3px solid rgba(189, 188, 188, 0.637)!important;">
                        <div class="d-flex justify-content-between">
                            <div class="d-flex">
                                <span @click="handleClick(pagamento.cartao)" class="d-flex color-white align-items-center justify-content-center" style="cursor:pointer;color: #e5e5e5; border: 1px solid transparent; border-radius:50%; width: 18px; height:18px; background: #1b56d6;">1</span>
                                <strong style="margin-left:10px">Cartão de Crédito</strong>
                            </div>
                            <small>à vista</small>
                        </div>
                        <div v-if="pagamento.cartao.showCartao">
                            <div class="d-flex" style="margin-top:20px" >
                                <div>
                                    <small>Nome do Cartão</small>
                                    <br>
                                    <input type="text" v-model="pagamento.cartao.nome" style="font-size:15px; padding: 5px" >
                                </div>
                                <div style="margin-left:50px; ">
                                    <small>CVC</small>
                                    <br>
                                    <input type="number" v-model="pagamento.cartao.cvc" style="font-size:15px; padding: 5px; width:100px!important" >
                                </div>
                                <br>
                            </div>
                            <div style="margin-top: 20px">
                                <small>Número do Cartão</small>
                                <br>
                                <input type="number" v-model="pagamento.cartao.numero" style="font-size:15px; padding: 5px" >
                            </div>
                        </div>
                    </div>
                    <div class="card "  style="margin-top: 5px; padding: 10px 10px;cursor:pointer; color: #636363; border-bottom: 3px solid rgba(189, 188, 188, 0.637)!important;">
                        <div class="d-flex justify-content-between">
                            <div class="d-flex">
                                <span @click="handleClick(pagamento.boleto)" class="d-flex color-white align-items-center justify-content-center" style="color: #e5e5e5; border: 1px solid transparent; border-radius:50%; width: 18px; height:18px; background: #1b56d6;">2</span>
                                <strong style="margin-left:10px">Boleto</strong>
                            </div>
                            <small>à vista</small>
                        </div>
                        <div v-if="pagamento.boleto.showBoleto">
                            <div class="d-flex" style="margin-top:20px" >
                                <div>
                                    <small>Codigo Boleto</small>
                                    <br>
                                    <input :disabled="true" type="text" v-model="pagamento.boleto.barcod" style="font-size:15px; padding: 5px" >
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="card "  style="margin-top: 5px; padding: 10px 10px;cursor:pointer; color: #636363; border-bottom: 3px solid rgba(189, 188, 188, 0.637)!important;">
                        <div class="d-flex justify-content-between">
                            <div class="d-flex">
                                <span @click="handleClick(pagamento.debito)" class="d-flex color-white align-items-center justify-content-center" style="color: #e5e5e5; border: 1px solid transparent; border-radius:50%; width: 18px; height:18px; background: #1b56d6;">3</span>
                                <strong style="margin-left:10px">Cartão de Debito</strong>
                            </div>
                            <small>à vista</small>
                        </div>
                        <div v-if="pagamento.debito.showDebito">
                            <div class="d-flex" style="margin-top:20px" >
                                <div>
                                    <small>Número do Cartão</small>
                                    <br>
                                    <input  type="text" v-model="pagamento.debito.numero" style="font-size:15px; padding: 5px" >
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="card "  style="margin-top: 5px; padding: 10px 10px;cursor:pointer; color: #636363; border-bottom: 3px solid rgba(189, 188, 188, 0.637)!important;">
                        <div class="d-flex justify-content-between">
                            <div class="d-flex">
                                <span @click="handleClick(pagamento.pix)" class="d-flex color-white align-items-center justify-content-center" style="color: #e5e5e5; border: 1px solid transparent; border-radius:50%; width: 18px; height:18px; background: #1b56d6;">2</span>
                                <strong style="margin-left:10px">Pix</strong>
                            </div>
                            <small>à vista</small>
                        </div>
                        <div v-if="pagamento.pix.showPix">
                            <div class="d-flex" style="margin-top:20px" >
                                <div>
                                    <small>Pix Copia e Cola</small>
                                    <br>
                                    <input :disabled="true" type="text" v-model="pagamento.pix.chavepix" style="font-size:15px; padding: 5px" >
                                </div>
                            </div>
                        </div>
                    </div>
                    <div style="float:right; align-text:right">
                        <h3>R${{'14,00'}}</h3>
                    </div>
                </div>
            </div>
        </div>
                <div style="background:#e5e5e5" class="footer ">
                    <button class="btn" style="margin-right:10px!important; border-color:#db2525; background: #db2525;" @click="handleEmitSale">Voltar</button>
                    <button class="btn" @click="handleEmitSale">Enviar</button>
                </div>
    </div>
</template>

<script>
export default {
    props:{
        pagamento:{
            type: Object
        },
    },
    methods:{
        handleClick(item){
            console.log(item == this.pagamento.cartao )
            if(this.pagamento.debito == item){
                this.pagamento.debito.showDebito = !this.pagamento.debito.showDebito
                return;
            }

            if(this.pagamento.boleto == item){
                this.pagamento.boleto.showboleto = !this.pagamento.boleto.showboleto
                return;
            }

            if(this.pagamento.cartao == item){
                this.pagamento.cartao.showcartao = !this.pagamento.cartao.showcartao
                return;
            }
        }
    }
}
</script>

<style>

</style>