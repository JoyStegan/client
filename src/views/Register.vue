<template>
    <div id="register">
        <div class="body"></div>
		<div class="grad"></div>
		<div class="header">
			<div id="title">Vision<span>Listen</span></div>
		</div>
		<br>
		<div class="login">
			<form @submit.prevent="register">
                <input style="margin-bottom: 10px;" v-model="registerData.name" type="text" placeholder="Name" name="user"><br>
				<input type="text" v-model="registerData.email" placeholder="Email" name="email"><br>
				<input type="password" v-model="registerData.password" placeholder="Password" name="password"><br>
				<input type="submit" class="btn btn-primary" value="Register">
			</form>
                <h6 style="color:white">Already have an account? </h6> 
                <button type="button" id="login-btn" @click="changePage('login')">Login HERE</button>
		</div>
    </div>
</template>

<script>
import axios from '../../config/axios'
import Swal from 'sweetalert2'

export default {
    name: 'Register',
    data () {
        return {
            registerData: {
                name: '',
                email: '',
                login: ''
            },
						Toast: Swal.mixin({
							toast: true,
							position: 'top-end',
							showConfirmButton: false,
							timer: 3000
						})
        }
    },
    methods: {
        register() {
            axios({
                method: 'post',
                data: {
                    name: this.registerData.name,
                    email: this.registerData.email,
                    password: this.registerData.password
                },
                url: `/register`
            })
                .then(user => {
                    console.log('Register success')
										this.registerData.name = ''
										this.registerData.email = ''
										this.registerData.password = ''
										this.changePage('login')
										Toast.fire({
											icon: 'success',
											title: 'Signed in successfully'
										})
                })
                .catch(err => {
                    console.log(err)
                })
				},
				changePage: function(value){
            this.$emit('change-page', value);
        }
    }

}
</script>

<style>
@import url(https://fonts.googleapis.com/css?family=Exo:100,200,400);
@import url(https://fonts.googleapis.com/css?family=Source+Sans+Pro:700,400,300);

#login-btn {
    cursor: pointer;
    border-radius: 3px;
    font-weight: bold;
	font-size: 15px;
	height: 45px;
	width: 140px;
	background-color: #28A71A;
	color: white;
    border: 0px;
	transition: all 0.1s ease-in-out;
}

#login-btn:hover {
	background-color: #34495e;
	color: white;
	font-weight: bold;
}

body{
	margin: 0;
	padding: 0;
	background: #fff;

	color: #fff;
	font-family: Arial;
	font-size: 12px;
}

.body{
	position: absolute;
	top: -20px;
	left: -20px;
	right: -40px;
	bottom: -20px;
	width: auto;
	height: auto;
	background-image: url(https://ipqi.org/wp-content/uploads/2015/07/b3c40392922e11e49ac59adf0a168030.jpg);
	background-size: cover;
	-webkit-filter: blur(4px);
	z-index: 0;
}

.grad{
	position: absolute;
	top: -20px;
	left: -20px;
	right: -40px;
	bottom: -40px;
	width: auto;
	height: auto;
	background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,rgba(0,0,0,0)), color-stop(100%,rgba(0,0,0,0.65))); /* Chrome,Safari4+ */
	z-index: 1;
	opacity: 0.7;
}

.header{
	position: absolute;
	top: calc(50% - 35px);
	left: calc(50% - 255px);
	z-index: 2;
}

.header div{
	float: left;
	color: #fff;
	font-family: 'Exo', sans-serif;
	font-size: 35px;
	font-weight: 200;
}

.header div span{
	color: #5379fa !important;
}

.login{
	position: absolute;
	top: calc(50% - 75px);
	left: calc(50% - 50px);
	height: 150px;
	width: 350px;
	padding: 10px;
	z-index: 2;
}

.login input[type=text]{
	width: 250px;
	height: 30px;
	background: transparent;
	border: 1px solid rgba(255,255,255,0.6);
	border-radius: 2px;
	color: #fff;
	font-family: 'Exo', sans-serif;
	font-size: 16px;
	font-weight: 400;
	padding: 4px;
}

.login input[type=password]{
	width: 250px;
	height: 30px;
	background: transparent;
	border: 1px solid rgba(255,255,255,0.6);
	border-radius: 2px;
	color: #fff;
	font-family: 'Exo', sans-serif;
	font-size: 16px;
	font-weight: 400;
	padding: 4px;
	margin-top: 10px;
}

.login input[type=button]{
	width: 260px;
	height: 35px;
	background: #fff;
	border: 1px solid #fff;
	cursor: pointer;
	border-radius: 2px;
	color: #a18d6c;
	font-family: 'Exo', sans-serif;
	font-size: 16px;
	font-weight: 400;
	padding: 6px;
	margin-top: 10px;
}

.login input[type=button]:hover{
	opacity: 0.8;
}

.login input[type=button]:active{
	opacity: 0.6;
}

.login input[type=text]:focus{
	outline: none;
	border: 1px solid rgba(255,255,255,0.9);
}

.login input[type=password]:focus{
	outline: none;
	border: 1px solid rgba(255,255,255,0.9);
}

.login input[type=button]:focus{
	outline: none;
}

::-webkit-input-placeholder{
   color: rgba(255,255,255,0.6);
}

::-moz-input-placeholder{
   color: rgba(255,255,255,0.6);
}
</style>