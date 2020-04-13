<template>
  <div id="Ferramentas"> 
      <select v-model="caixaSel">
          <option value="" selected disabled> Selecione uma caixa</option>>
          <option v-for="(caixa, index) in caixinhas" :key="index" :value="index">
                    {{ caixa.titulo }}
          </option>
      </select>
      <div id="paleta">
          <div class="cor" :style="cor" v-for="(cor, index) in cores" :key="index" @click="alteraCor(cor)"></div>
      </div>
        <input type="text" placeholder="Digite o nome da caixa" v-model="titulo"/>
          <button @click="alterarTexto">Ok</button>
  </div>
</template>

<script>


export default {
    name: "Ferramentas",
    props: ['caixinhas'],
    data: function() {
        return {
            cores: ['background: brown', 'background: white', 'background: green'],
            caixaSel: '',
            titulo: ''
        }
    }, methods: {
        alteraCor: function(cor){
            this.$emit('alteraCor', {
                cor: cor,
                caixa: this.caixaSel
            })
        }, alterarTexto: function(){
            this.$emit('alterouTexto', {
                titulo: this.titulo,
                caixa: this.caixaSel
            })
        }
    }
}
</script>

<style>
    #Ferramentas {
        width: 380px;
        height: 150px;
        border: 1px solid #ffffff;
        margin: 5px auto 0 auto;
        padding: 10px;
    }
    #Ferramentas select {
        width: 360px;
        margin-bottom: 5px;
        }
        #paleta {
        width: 380px;
        height: 150px;
        display: flex;
        }
        .cor {
        width: 60px;
        height: 60px;
        border: 1px solid #ffffff;
        margin-right: 5px;
        }
</style>