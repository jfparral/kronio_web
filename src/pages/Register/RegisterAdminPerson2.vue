<template>
	<div class="login">
		<b-navbar class="is-fixed-top is-paddingless">
			<template slot="brand">
				<a class="navbar-item link" href="https://kronio.io">
					<LogoSVG />
				</a>
			</template>
			<template slot="end">
				<div class="navbar-item">
					<a class="color-login" href="/login">Iniciar Sesión</a>
				</div>
			</template>
		</b-navbar>
		<div class="columns margin-top-register">
			<div class="column is-1"></div>
			<div class="column is-5 is-mobile is-vcentered">
				<div class="box margin-top-form">
					<article class="media">
						<div class="media-content">
							<div class="content">
								<div class="columns">
									<div class="column is-full">
										<p class="subtitle is-4 title-register has-text-primary has-text-centered">
											Datos del administrador
										</p>
									</div>
								</div>
								<div class="columns is-centered">
									<div class="column is-full">
										<section class="margin-button">
											<div class="field">
												<p class="control has-icons-left has-icons-right">
													<b-input
														class="form-fields"
														v-model="register_form.id"
														@keyup.enter.native="continuar()"
														placeholder="Identificación"
													>
													</b-input>
												</p>
											</div>
											<div class="field">
												<p class="control has-icons-left has-icons-right">
													<b-input
														class="form-fields"
														v-model="register_form.address"
														@keyup.enter.native="continuar()"
														placeholder="Dirección"
													>
													</b-input>
												</p>
											</div>
											<div class="columns line-phone">
												<div class="column is-4">
													<b-select
														class="select-prefix"
														v-model="register_form.prefix"
														placeholder="Prefijo"
													>
														<option v-for="option in data" :value="option" :key="option">
															{{ option }}
														</option>
													</b-select>
												</div>
												<div class="column is-8">
													<p class="control input-phone has-icons-left has-icons-right">
														<b-input
															class="form-field-phone"
															v-model="register_form.phone"
															@keyup.enter.native="continuar()"
															placeholder="Telefono"
														>
														</b-input>
													</p>
												</div>
											</div>
											<div class="field">
												<b-datepicker
													class="form-fields"
													v-model="register_form.birthday"
													placeholder="Fecha de nacimiento"
													icon="calendar-today"
													trap-focus
												>
												</b-datepicker>
											</div>

											<div class="field has-text-centered">
												<b-button
													@click="continuar()"
													type="is-primary"
													expanded
													class="btn-register body"
													>Continuar</b-button
												>
											</div>
										</section>
									</div>
								</div>
							</div>
						</div>
					</article>
				</div>
			</div>
			<div class="column is-6">
				<img class="is-pulled-right" src="../../assets/adm1_4.png" />
			</div>
		</div>
	</div>
</template>

<script lang="ts">
import PageBase from '@/utils/page_base.utils';
import { Component } from 'vue-property-decorator';
import LogoSVG from '@/components/LogoSVG.vue';
import { RegisterAdminPerson2Form } from '@/store/auth.module/signup.type';

@Component({
	components: { LogoSVG },
})
export default class RegisterAdminPerson2 extends PageBase {
	public register_form: RegisterAdminPerson2Form = new RegisterAdminPerson2Form({});

	public async created() {
		await super.created();
	}

	public async continuar() {
		this.$router.push('/login');
	}

	public data = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
}
</script>

<style lang="scss">
body {
	font-family: Poppins !important;
	font-style: normal !important;
}
.select {
	width: 100% !important;
	height: 2.5em !important;

	select {
		width: 100% !important;
		padding-left: 12% !important;
		padding-right: 3% !important;
		padding-bottom: 0% !important;
		padding-top: 0% !important;
		height: 2.5em !important;
	}
}

.select-prefix {
	margin-top: 9% !important;
	@media screen and (max-width: 1772px) {
		font-size: 16px;
		padding-top: 1%;
	}

	@media screen and (max-width: 1440px) {
		font-size: 12px;
		padding-top: 1%;
	}

	@media screen and (max-width: 1596px) {
		margin-top: 7% !important;
	}

	@media screen and (max-width: 768px) {
		margin-top: 0% !important;
		width: 99%;
		font-size: 18px;
		padding-left: 1%;
	}

	@media screen and (max-width: 600px) {
		margin-top: 0% !important;
		width: 97%;
		padding-left: 1%;
	}

	@media screen and (max-width: 450px) {
		margin-top: 0% !important;
		width: 100%;
		padding-left: 0%;
	}
}

.login {
	.line-phone {
		margin-left: 7%;
		margin-right: 7%;
	}

	.form-field-phone {
		padding-top: 4%;
		padding-bottom: 4%;
		@media screen and (max-width: 1596px) {
			padding-top: 4%;
			padding-bottom: 4%;
		}

		@media screen and (max-width: 768px) {
			padding-top: 0%;
			padding-bottom: 0%;
			padding-left: 1%;
			padding-right: 1%;
		}

		@media screen and (max-width: 700px) {
			padding-top: 0%;
			padding-bottom: 0%;
			padding-left: 0%;
			padding-right: 0%;
		}
	}

	.message-float {
		position: absolute;
		z-index: 1000;
		margin-top: 5%;
		margin-left: 35%;
		margin-right: auto;
	}
	.navbar {
		background: #8969eb;
		box-shadow: 0 3px 3px rgba(0, 0, 0, 0.05);

		.navbar-brand {
			margin-left: 8%;
		}

		@media screen and (max-width: 1023px) {
			.navbar-brand {
				margin-left: 3%;
			}
		}

		.logo-svg {
			width: 130px;
			height: auto !important;
		}

		@media screen and (max-width: 1023px) {
			.logo-svg {
				width: 100px;
			}
		}

		.link {
			margin-right: 5% !important;
		}

		@media screen and (max-width: 1023px) {
			.link {
				margin-left: 0;
			}
		}
	}

	.color-login {
		color: #ffffff !important;
	}

	.margin-top-register {
		margin-top: 2%;
	}

	.margin-top-form {
		margin-top: 12%;
		width: 70%;
		margin-left: 10%;
		height: calc(80vh - 4rem);

		@media screen and (max-width: 1400px) {
			width: 75%;
			margin-top: 15%;
			height: calc(61vh - 4rem);
		}

		@media screen and (max-width: 1080px) {
			width: 70%;
			margin-top: 3%;
			height: calc(61vh - 4rem);
		}

		@media screen and (max-width: 768px) {
			width: 90%;
			margin-top: 3%;
			height: calc(90vh - 4rem);
		}

		@media screen and (max-width: 600px) {
			width: 90%;
			margin-top: 3%;
			height: calc(70vh - 4rem);
		}
	}

	.title-register {
		padding-top: 8%;
	}

	.btn-register {
		padding-top: 5% !important;
		padding-bottom: 10% !important;
		width: 80%;
		display: block;
		margin-top: 5%;
		margin-left: 10% !important;
		// margin-right: 5% !important;
		background: #335eea;
		border-radius: 3px;
	}

	.form-fields {
		margin-left: 10% !important;
		margin-right: 10% !important;
	}

	.input {
		padding-bottom: 8% !important;
		padding-top: 8% !important;
	}

	.password-input {
		margin-bottom: 0% !important;
	}

	.password-label {
		margin-bottom: 2% !important;
		margin-right: 10% !important;
		color: #7a7979;
		font-size: 15px;
	}
}
</style>
