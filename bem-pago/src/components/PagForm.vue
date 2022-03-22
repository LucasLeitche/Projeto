<template>
    <div>
        <div class="container">
            <div class="d-flex flex-direction-column" v-if="!donePayment">
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
                    <div class="card " @click.stop="handleClickOpen(pagamento.cartao)"  style="cursor:pointer; margin-top: 5px; padding: 10px 10px;color: #636363; border-bottom: 3px solid rgba(189, 188, 188, 0.637)!important;">
                        <div class="d-flex justify-content-between">
                            <div class="d-flex">
                                <span class="d-flex color-white align-items-center justify-content-center"  :style="pagamento.cartao.selected ? 'background: green': ''" style="color: #e5e5e5; border: 1px solid transparent; border-radius:50%; width: 18px; height:18px; background: #1b56d6;">1</span>
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
                                    <input type="number" v-model="pagamento.cartao.cvc"  style="font-size:15px; padding: 5px; width:100px!important" >
                                </div>
                                <br>
                            </div>
                            <div class="d-flex align-items-end" style="margin-top: 20px; ">
                                <div>
                                    <small>Número do Cartão</small>
                                    <br>
                                    <input type="number" v-model="pagamento.cartao.numero" style="font-size:15px; padding: 5px" >
                                </div>
                                <div class="d-flex justify-content-center" style="width:100%!important;max-height:25px!important">
                                    <button class="btn" @click.stop="handleClickSave(pagamento.cartao)" style="font-size:12px!important">Salvar</button>
                                    <button class="btn" @click.stop="handleClickClose(pagamento.cartao)" style="border-color:#db2525; margin-left:20px; background: #db2525; font-size:12px!important">Cancelar</button>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="card " @click.stop="handleClickOpen(pagamento.boleto)"  style="margin-top: 5px; padding: 10px 10px;cursor:pointer; color: #636363; border-bottom: 3px solid rgba(189, 188, 188, 0.637)!important;">
                        <div class="d-flex justify-content-between">
                            <div class="d-flex">
                                <span  class="d-flex color-white align-items-center justify-content-center" :style="pagamento.boleto.selected ? 'background: green': ''" style="color: #e5e5e5; border: 1px solid transparent; border-radius:50%; width: 18px; height:18px; background: #1b56d6;">2</span>
                                <strong style="margin-left:10px">Boleto</strong>
                            </div>
                            <small>à vista</small>
                        </div>
                        <div v-if="pagamento.boleto.showBoleto">
                            <div class="d-flex align-items-end" style="margin-top:20px" >
                                <div>
                                    <small>Codigo Boleto</small>
                                    <br>
                                    <input :disabled="true" type="text" v-model="pagamento.boleto.barcod" style="font-size:15px; padding: 5px" >
                                </div>
                                 <div class="d-flex justify-content-center" style="width:100%!important;max-height:25px!important;">
                                    <button class="btn" @click.stop="handleClickSave(pagamento.boleto)" style="font-size:12px!important">Salvar</button>
                                    <button class="btn" @click.stop="handleClickClose(pagamento.boleto)" style="border-color:#db2525; margin-left:20px; background: #db2525; font-size:12px!important">Cancelar</button>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="card " @click.stop="handleClickOpen(pagamento.debito)"  style="margin-top: 5px; padding: 10px 10px;cursor:pointer; color: #636363; border-bottom: 3px solid rgba(189, 188, 188, 0.637)!important;">
                        <div class="d-flex justify-content-between">
                            <div class="d-flex">
                                <span class="d-flex color-white align-items-center justify-content-center" :style="pagamento.debito.selected ? 'background: green': ''" style="color: #e5e5e5; border: 1px solid transparent; border-radius:50%; width: 18px; height:18px; background: #1b56d6;">3</span>
                                <strong style="margin-left:10px">Cartão de Debito</strong>
                            </div>
                            <small>à vista</small>
                        </div>
                        <div v-if="pagamento.debito.showDebito">
                            <div class="d-flex align-items-end" style="margin-top:20px;" >
                                <div>
                                    <small>Número do Cartão</small>
                                    <br>
                                    <input  type="text" v-model="pagamento.debito.numero" style="font-size:15px; padding: 5px" >
                                </div>
                                <div class="d-flex justify-content-center" style="width:100%!important;max-height:25px!important;">
                                    <button class="btn" @click.stop="handleClickSave(pagamento.debito)" style="font-size:12px!important">Salvar</button>
                                    <button class="btn" @click.stop="handleClickClose(pagamento.debito)" style="border-color:#db2525; margin-left:20px; background: #db2525; font-size:12px!important">Cancelar</button>
                                </div>  
                            </div>
                        </div>
                    </div>
                    <div class="card " @click.stop="handleClickOpen(pagamento.pix)" style="margin-top: 5px; padding: 10px 10px;cursor:pointer; color: #636363; border-bottom: 3px solid rgba(189, 188, 188, 0.637)!important;">
                        <div class="d-flex justify-content-between">
                            <div class="d-flex">
                                <span  class="d-flex color-white align-items-center justify-content-center" :style="pagamento.pix.selected ? 'background: green': ''" style="color: #e5e5e5; border: 1px solid transparent; border-radius:50%; width: 18px; height:18px; background: #1b56d6;">2</span>
                                <strong style="margin-left:10px">Pix</strong>
                            </div>
                            <small>à vista</small>
                        </div>
                        <div v-if="pagamento.pix.showPix">
                            <div class="d-flex align-items-end" style="margin-top:20px" >
                                <div>
                                    <small>Pix Copia e Cola</small>
                                    <br>
                                    <input :disabled="true" type="text" v-model="pagamento.pix.chavepix" style="font-size:15px; padding: 5px" >
                                </div>
                                <div class="d-flex justify-content-center" style="width:100%!important;max-height:25px!important;">
                                    <button class="btn" @click.stop="handleClickSave(pagamento.pix)"  style="font-size:12px!important">Salvar</button>
                                    <button class="btn" @click.stop="handleClickClose(pagamento.pix)" style="border-color:#db2525; margin-left:20px; background: #db2525; font-size:12px!important">Cancelar</button>
                                </div>  
                            </div>
                        </div>
                    </div>
                    <div style="float:right; align-text:right">
                        <h3>R${{'14,00'}}</h3>
                    </div>
                </div>
            </div>
            <div class="d-flex flex-direction-column align-items-center" style="margin-top:30px!important" v-if="donePayment">
                <div class="d-flex justify-content-center">
                    <i class="fa fa-check-circle" style="color: #40b186; font-size: 55px"></i>
                </div>
                <div>
                    <h2 style="color: #40b186;">Compra Finalizada!</h2>
                </div>
                <div class="container">
                    <div style="margin: 15px 0">
                        <span style="margin-right:8px"><strong>Itens:</strong></span>
                        <span style="padding: 0 1px" v-for="(ped, index) in pedido.items" :key="index">{{ped}} <span v-if="index < pedido.items.length - 1">,</span> </span>
                    </div>
                    <div style="margin: 15px 0">
                        <span style="margin-right:8px"><strong>Quantidade: </strong> <span>{{pedido.quantidade}}</span></span>
                    </div>
                    <div style="margin: 15px 0">
                        <span v-if="pedido.observacao" style="margin-right:8px"><strong> Observação: </strong> <span>{{pedido.observacao}}</span></span>
                    </div>
                    <div style="margin: 15px 0">
                        <span> <strong>Forma de pagamento: </strong> {{
                            pedido.pagamento.cartao.selected ? 'Cartão' :
                            pedido.pagamento.debito.selected ? 'Debito' :
                            pedido.pagamento.boleto.selected ? 'Boleto' :
                            pedido.pagamento.pix.selected ? 'Pix':
                            'Não informado'
                            }}</span>
                    </div>
                </div>
            </div>
        </div>
        <div style="background:#e5e5e5" class="footer ">
            <button class="btn" @click="handleBack" style="margin-right:10px!important; border-color:#db2525; background: #db2525;" >Voltar</button>
            <button class="btn" v-if="!donePayment" @click="handleDonePayment">Enviar</button>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return {
            donePayment: false
        }
    },
    props:{
        pagamento:{
            type: Object
        },
        pedido:{
            type: Object
        }
    },
    methods:{
        handleBack(){
            this.$emit('retornar')
        },
        handleDonePayment(){
            this.donePayment = true
        },
        handleClickOpen(item){
            var self = this;
            if(item == this.pagamento.cartao && !this.pagamento.cartao.showDebito && !this.pagamento.boleto.showBoleto && !this.pagamento.pix.showPix){
                this.$nextTick( async () =>{
                    await self.$set(self.pagamento.cartao, 'showCartao', true)
                })
                return;
            }
            if(item == this.pagamento.debito && !this.pagamento.debito.showDebito && !this.pagamento.boleto.showBoleto && !this.pagamento.pix.showPix){
                this.$nextTick(async () =>{
                    await self.$set(self.pagamento.debito, 'showDebito', true)
                })
                return;
            }

            if(item == this.pagamento.boleto && !this.pagamento.debito.showDebito && !this.pagamento.cartao.showCartao && !this.pagamento.pix.showPix){
                this.$nextTick(function (){
                    self.$set(self.pagamento.boleto, 'showBoleto', true)
                })
                return;
            }

            if(item == this.pagamento.pix && !this.pagamento.debito.showDebito && !this.pagamento.boleto.showBoleto && !this.pagamento.cartao.showCartao){
                self.$set(self.pagamento.pix, 'showPix', true)
                return;
            }
        },
        handleClickClose(item){
            if(item == this.pagamento.cartao){
                this.pagamento.cartao = {}
                this.$set(this.pagamento.cartao, 'selected', false)
                this.$set(this.pagamento.cartao, 'showCartao', false)
                return;
            }
            if(item == this.pagamento.debito){
                this.pagamento.cartao = {}
                this.$set(this.pagamento.debito, 'selected', false)
                this.$set(this.pagamento.debito, 'showDebito', false)
                return;
            }
            if(item == this.pagamento.boleto){
                this.pagamento.cartao = {}
                this.$set(this.pagamento.boleto, 'selected', false)
                this.$set(this.pagamento.boleto, 'showBoleto', false)
                return;
            }
            if(item == this.pagamento.pix){
                this.pagamento.cartao = {}
                this.$set(this.pagamento.pix, 'selected', false)
                this.$set(this.pagamento.pix, 'showPix', false)
                return;
            }

        },
        handleClickSave(item){
            if(item == this.pagamento.cartao){
                this.$set(this.pagamento.cartao, 'selected', true)
                this.$set(this.pagamento.cartao, 'showCartao', false)
                return;
            }
            if(item == this.pagamento.debito){
                this.$set(this.pagamento.debito, 'selected', true)
                this.$set(this.pagamento.debito, 'showDebito', false)
                return;
            }
            if(item == this.pagamento.boleto){
                this.$set(this.pagamento.boleto, 'selected', true)
                this.$set(this.pagamento.boleto, 'showBoleto', false)
                return;
            }
            if(item == this.pagamento.pix){
                this.$set(this.pagamento.pix, 'selected', true)
                this.$set(this.pagamento.pix, 'showPix', false)
                return;
            }

        }
    },

}
</script>

<style>

</style>