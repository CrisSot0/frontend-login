<template>
    <v-card class="cardLogin">
        <v-card-title class="title">Bienvenido!!!</v-card-title>
        <v-card-text>
            <v-row justify="center" align="center">
                <v-col cols="4" align-self="center">
                    <img src="../../assets/images/perron.jpg" class="imgLogin">
                </v-col>
                <v-col cols="8" align-self="center">
                    <v-form ref="formLogin">
                    <v-text-field label="Ingresa tu correo electronico" 
                              placeholder="ejemplo: hola@outlook.com"
                              v-model="correoElectronico"
                              :rules="validarCorreo"
                    />
                    <v-text-field label="Ingresa tu contraseña" 
                              placeholder="ejemplo: 12345678"
                              v-model="password"
                              :rules="validarPassword"
                    />
                    </v-form>
                </v-col>
            </v-row>
        </v-card-text>
        <v-card-actions>
            <v-btn
            class="btnLogin"
            rounded
            block
            @click="loginBackend"
            >
                Login
            </v-btn>
        </v-card-actions>
    </v-card>
</template>

<script>
export default {
    data() {
        return {
            correoElectronico: '',
            validarCorreo: [
            v => !v || /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(v) || 'El email tiene que ser valido'
            ],
            password: '',
            validarPassword: [
                value => value.length >= 6 || 'Minimo 6 caracteres',
            ]
        }
    },
    methods: {
        loginBackend () {
            const valid = this.$refs.formLogin.validate()
            if (valid){
                alert('Presionaste el boton vale')
            } else {
                alert('No cumpliste las reglas')
            }
        }
    }
}
</script>

<style scoped>
    .cardLogin{
        background-color: #546E7A;
        border-radius: 10px;
        width: 500px;
        height: 300px;

    }
    .imgLogin{
        width:100%;
        height: 100%;
    }
    .btnLogin{
        color: white!important;
        background-color: black!important;
    }
    .title{
        font-size: 30px;
        justify-content: center;
        color: whitesmoke;
        font-weight: 700;
    }
</style>