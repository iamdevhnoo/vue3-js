<template>
	<div class="flex items-center min-h-screen p-6 pt-32 bg-gray-50 dark:bg-gray-900">
		<div
			class="flex-1 h-full max-w-4xl mx-auto overflow-hidden bg-white rounded-lg shadow-xl dark:bg-gray-800"
		>
			<div class="flex flex-col overflow-y-auto md:flex-row">
				<div class="h-32 md:h-auto md:w-1/2">
					<img
						aria-hidden="true"
						class="object-cover w-full h-full dark:hidden"
						src="@/assets/img/create-account-office.jpeg"
						alt="Office"
					/>
					<img
						aria-hidden="true"
						class="hidden object-cover w-full h-full dark:block"
						src="@/assets/img/create-account-office-dark.jpeg"
						alt="Office"
					/>
				</div>

				<div class="flex items-center justify-center p-6 sm:p-12 md:w-1/2">
					<div class="w-full">
						<h1 class="mb-4 text-xl font-semibold text-gray-700 dark:text-gray-200">
							สมัครสมาชิกใหม่
						</h1>

						<form @submit.prevent="onSubmit">
							<label class="block mb-2 text-sm text-gray-700" for="fullname">ชื่อ-สกุล</label>
							<input
								v-model="fullname"
								class="w-full px-3 py-2 leading-tight text-gray-700 border rounded shadow appearance-none"
								id="fullname"
								type="text"
							/>
							<div v-if="v$.fullname.$error" class="mt-2 text-sm text-red-500">
								{{ v$.fullname.$errors[0]?.$message }}
							</div>

							<label class="block mt-3 mb-2 text-sm text-gray-700" for="username">ชื่อผู้ใช้</label>
							<input
								v-model="username"
								class="w-full px-3 py-2 leading-tight text-gray-700 border rounded shadow appearance-none"
								id="username"
								type="text"
							/>
							<div v-if="v$.username.$error" class="mt-2 text-sm text-red-500">
								{{ v$.username.$errors[0]?.$message }}
							</div>

							<label class="block mt-3 mb-2 text-sm text-gray-700" for="tel">โทรศัพท์</label>
							<input
								v-model="tel"
								class="w-full px-3 py-2 leading-tight text-gray-700 border rounded shadow appearance-none"
								id="tel"
								type="text"
							/>
							<div v-if="v$.tel.$error" class="mt-2 text-sm text-red-500">
								{{ v$.tel.$errors[0]?.$message }}
							</div>

							<label class="block mt-3 mb-2 text-sm text-gray-700" for="email">อีเมล์</label>
							<input
								v-model="email"
								class="w-full px-3 py-2 leading-tight text-gray-700 border rounded shadow appearance-none"
								id="email"
								type="text"
								autocomplete="email"
							/>
							<div v-if="v$.email.$error" class="mt-2 text-sm text-red-500">
								{{ v$.email.$errors[0]?.$message }}
							</div>

							<label class="block mt-3 mb-2 text-sm text-gray-700" for="password">รหัสผ่าน</label>
							<input
								v-model="password"
								class="w-full px-3 py-2 leading-tight text-gray-700 border rounded shadow appearance-none"
								id="password"
								type="password"
								autocomplete="current-password"
							/>
							<div v-if="v$.password.$error" class="mt-2 text-sm text-red-500">
								{{ v$.password.$errors[0]?.$message }}
							</div>

							<label class="block mt-3 mb-2 text-sm text-gray-700" for="confirm_password"
								>ยืนยันรหัสผ่าน</label
							>
							<input
								v-model="password_confirmation"
								class="w-full px-3 py-2 leading-tight text-gray-700 border rounded shadow appearance-none"
								id="password_confirmation"
								type="password"
								autocomplete="current-password"
							/>
							<div v-if="v$.password_confirmation.$error" class="mt-2 text-sm text-red-500">
								{{ v$.password_confirmation.$errors[0]?.$message }}
							</div>

							<p class="my-4"></p>

							<label class="flex items-center dark:text-gray-400">
								<input
									type="checkbox"
									class="text-purple-600 form-checkbox focus:border-purple-400 focus:outline-none focus:shadow-outline-purple dark:focus:shadow-outline-gray"
								/>
								<span class="ml-2"
									>ฉันยอมรับ <span class="underline">เงื่อนไขการใช้งานระบบ</span>
								</span>
							</label>

							<!--<input
								type="button"
								class="block w-full px-4 py-2 mt-4 text-sm font-medium leading-5 text-center text-white transition-colors duration-150 bg-purple-600 border border-transparent rounded-lg cursor-pointer active:bg-purple-600 hover:bg-purple-700"
								value="สมัครสมาชิก"
							/>-->
							<button
								@click="submitForm"
								class="block w-full px-4 py-2 mt-4 text-sm font-medium leading-5 text-center text-white transition-colors duration-150 bg-purple-600 border border-transparent rounded-lg cursor-pointer active:bg-purple-600 hover:bg-purple-700"
							>
								สมัครสมาชิก
							</button>
						</form>

						<p class="my-8"></p>

						<button
							class="flex items-center justify-center w-full px-4 py-2 text-sm font-medium leading-5 transition-colors duration-150 border border-gray-300 rounded-lg dark:text-gray-400 active:bg-transparent hover:border-gray-500 focus:border-gray-500 active:text-gray-500 focus:outline-none focus:shadow-outline-gray"
						>
							<svg class="w-4 h-4 mr-2" aria-hidden="true" viewBox="0 0 24 24" fill="currentColor">
								<path
									d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"
								/>
							</svg>
							Github
						</button>
						<button
							class="flex items-center justify-center w-full px-4 py-2 mt-4 text-sm font-medium leading-5 transition-colors duration-150 border border-gray-300 rounded-lg dark:text-gray-400 active:bg-transparent hover:border-gray-500 focus:border-gray-500 active:text-gray-500 focus:outline-none focus:shadow-outline-gray"
						>
							<svg class="w-4 h-4 mr-2" aria-hidden="true" viewBox="0 0 24 24" fill="currentColor">
								<path
									d="M23.954 4.569c-.885.389-1.83.654-2.825.775 1.014-.611 1.794-1.574 2.163-2.723-.951.555-2.005.959-3.127 1.184-.896-.959-2.173-1.559-3.591-1.559-2.717 0-4.92 2.203-4.92 4.917 0 .39.045.765.127 1.124C7.691 8.094 4.066 6.13 1.64 3.161c-.427.722-.666 1.561-.666 2.475 0 1.71.87 3.213 2.188 4.096-.807-.026-1.566-.248-2.228-.616v.061c0 2.385 1.693 4.374 3.946 4.827-.413.111-.849.171-1.296.171-.314 0-.615-.03-.916-.086.631 1.953 2.445 3.377 4.604 3.417-1.68 1.319-3.809 2.105-6.102 2.105-.39 0-.779-.023-1.17-.067 2.189 1.394 4.768 2.209 7.557 2.209 9.054 0 13.999-7.496 13.999-13.986 0-.209 0-.42-.015-.63.961-.689 1.8-1.56 2.46-2.548l-.047-.02z"
								/>
							</svg>
							Twitter
						</button>

						<p class="mt-2">
							<router-link
								to="/login"
								class="text-sm font-medium text-purple-600 dark:text-purple-400 hover:underline"
								>ฉันเป็นสมาชิกอยู่แล้ว ? เข้าสู่ระบบ</router-link
							>
						</p>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
import useValidate from "@vuelidate/core";
import { required, email, minLength, helpers, sameAs } from "@vuelidate/validators";
import http from "@/services/AuthService";
export default {
	data() {
		return {
			v$: useValidate(),
			fullname: "",
			username: "",
			tel: "",
			email: "",
			password: "",
			password_confirmation: "",
		};
	},
	methods: {
		submitForm() {
			this.v$.$validate();
			if (!this.v$.$error) {
				http
					.post("register", {
						fullname: this.fullname,
						username: this.username,
						tel: this.tel,
						email: this.email,
						password: this.password,
						password_confirmation: this.password_confirmation,
						role: "2",
					})
					.then((response) => {
						console.log(response.data);
						// เก็บข้อมูลลง localStorage
						localStorage.setItem("user", JSON.stringify(response.data));

						// เรียกใช้งาน popup ของ sweetalert2
						const Toast = this.$swal.mixin({
							toast: true,
							position: "top-end",
							showConfirmButton: false,
							timer: 1500,
							timerProgressBar: true,
							didOpen: (toast) => {
								toast.addEventListener("mouseenter", this.$swal.stopTimer);
								toast.addEventListener("mouseleave", this.$swal.resumeTimer);
							},
						});
						Toast.fire({
							icon: "success",
							title: "ลงทะเบียนสําเร็จ กำลังเข้าสู่ระบบ...",
						}).then(() => {
							// this.$router.push("/login");
							this.$router.push({ name: "Dashboard" });
						});
					})
					.catch((error) => {
						if (error.response) {
							// console.log(error.response.data);
							// console.log(error.response.status);
							// console.log(error.response.headers);
							if (error.response.status == 401) {
								alert(error.response.data.message);
								const Toast = this.$swal.mixin({
									toast: true,
									position: "top-end",
									showConfirmButton: false,
									timer: 1500,
									timerProgressBar: true,
									didOpen: (toast) => {
										toast.addEventListener("mouseenter", this.$swal.stopTimer);
										toast.addEventListener("mouseleave", this.$swal.resumeTimer);
									},
								});
								Toast.fire({
									icon: "error",
									title: error.response.data.message,
								});
							}
						}
					});
				// alert("Form Submitted!");
			} else {
				// alert("Form Not Submitted!");
			}
		},
	},
	validations() {
		return {
			fullname: {
				required: helpers.withMessage("ป้อนชื่อ-นามสกุลก่อน", required),
			},
			username: {
				required: helpers.withMessage("ป้อนชื่อผู้ใช้ก่อน", required),
			},
			tel: {
				required: helpers.withMessage("ป้อนเบอร์โทรศัพท์ก่อน", required),
			},
			email: {
				required: helpers.withMessage("ป้อนอีเมล์ก่อน", required),
				email: helpers.withMessage("รูปแบบอีเมล์ที่ป้อนไม่ถูกต้อง", email),
			},
			password: {
				required: helpers.withMessage("ป้อนรหัสผ่านก่อน", required),
				minLength: helpers.withMessage(
					({ $params }) => `รหัสผ่านต้องไม่น้อยกว่า ${$params.min} ตัวอักษร`,
					minLength(6)
				),
			},
			password_confirmation: {
				required: helpers.withMessage("ป้อนยืนยันรหัสผ่านก่อน", required),
				sameAs: helpers.withMessage("รหัสผ่านไม่ตรงกัน", sameAs(this.password)),
			},
		};
	},
};
</script>
