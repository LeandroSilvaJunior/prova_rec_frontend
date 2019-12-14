<template>
    <form>
        <label>Data emissão:</label>
        <input type="date" v-model="contaPagar.dataEmissao"><br>

        <label>Data vencimento:</label>
        <input type="date" v-model="contaPagar.dataVencimento"><br>

        <label>Valor:</label>
        <input type="number" v-model="contaPagar.valor"><br>

        <label>Data pagamento:</label>
        <input type="date" v-model="contaPagar.dataPagamento"><br>

        <label>Pessoa:</label>
        <select v-model="contaPagar.pessoa.id">
            <option v-for="p in pessoas" :key="p">{{p.nome}}</option>
        </select><br>

        <label>Tipo de despesa:</label>
        <select v-model="contaPagar.tipoDespesa.id">
            <option v-for="t in tiposDespesa" :key="t">{{t.nome}}</option>
        </select><br>

        <button @click="contaPagar">Salvar</button>
    </form>
</template>

<script>
    import axios from 'axios'

    export default {
        name: "cadastraConta",
        data() {
            return {
                contaPagar : {
                    dataEmissao : "",
                    dataVencimento : "",
                    valor : "",
                    tipoDespesa : "",
                    pessoa : ""
                },
                pessoas : [],
                tiposDespesa : []
            }
        },
        methods: {
            loadData() {
                axios.get('http://localhost:8080/pessoa').then(
                    response => { this.pessoas = response.data }
                ).catch(
                    error => {
                        alert('Serviço indisponivel!')
                        // eslint-disable-next-line no-console
                        console.log(error)
                    }
                )

                axios.get('http://localhost:8080/tipoDespesa').then(
                    response => { this.tiposDespesa = response.data }
                ).catch(
                    error => {
                        alert('Serviço indisponivel!')
                        // eslint-disable-next-line no-console
                        console.log(error)
                    }
                )
            },
            gravarConta() {
                axios.post('http://localhost:8080/contaPagar', this.contaPagar).catch(error => {
                    alert('Erro ao adicionar a conta')
                    // eslint-disable-next-line no-console
                    console.log(error)
                })
            }
        },
        mounted() {
            this.loadData()
        }
    }
</script>

<style scoped>

</style>