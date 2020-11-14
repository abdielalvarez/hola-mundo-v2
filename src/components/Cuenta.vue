<template>
    <div>
        <h2>Tipo de cuenta: {{cuenta}}</h2>
        <h2>Saldo: {{saldo}}</h2>
        <h2>Cuenta: {{estado ? 'Activa' : 'Desactivada'}}</h2>
        <div v-for="(servicio, index) in servicios" :key="index">
            {{index + 1}} - {{ servicio }}
        </div>
        <AccionSaldo
            texto="Aumentar Saldo"
            @accion="aumentar"
        />
        <AccionSaldo
            texto="Disminuir Saldo"
            :isDisabled="isDisabled"
            @accion="disminuir"
        />
        
    </div>
</template>

<script>
import AccionSaldo from './AccionSaldo';

export default {
    components: {
        AccionSaldo,
    },
    data() {
        return {
            saldo: 1000,
            cuenta: 'Visa',
            estado: true,
            servicios: ['giro', 'abono', 'transferencia'],
            isDisabled: false
        }
    },
    methods: {
        aumentar() {
            this.saldo += 100
            this.isDisabled = false
        }, 
        disminuir() {
            if (this.saldo === 0) {
                this.isDisabled = true
                alert('Saldo agotado')
                return
            }
            this.saldo -= 100
        }
    }
}
</script>

<style>

</style>