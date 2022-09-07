<template>
    <form @submit.prevent="handleSubmit">
        <div class="row container pt-3">
            <div class="mb-3 col-12 col-md-6" data-aos="fade-up">
                <div class="w-75 mx-auto">
                    <label for="firstName" class="form-label text-uppercase fw-bold">First name <span
                            class="text-danger">*</span></label>
                    <input type="text" class="form-control" id="firstName" name="firstName"
                        placeholder="Enter your first name" v-model="firstName" @blur="v$.firstName.$touch"
                        :class="{'is-invalid': validationStatus(v$.firstName)}">
                    <div v-if="v$.firstName.$error" class="invalid-feedback">First name field is required</div>
                </div>
            </div>
            <div class="mb-3 col-12 col-md-6" data-aos="fade-up" data-aos-delay="100">
                <div class="w-75 mx-auto">
                    <label for="gender" class="form-label text-uppercase fw-bold">Gender <span
                            class="text-danger">*</span></label>
                    <select name="gender" id="gender" class="form-control" v-model="gender" @blur="v$.gender.$touch"
                        :class="{'is-invalid': validationStatus(v$.gender)}">
                        <option value="male">Male</option>
                        <option value="female">Female</option>
                    </select>
                    <div v-if="v$.gender.$error" class="invalid-feedback">Gender field is required</div>
                </div>
            </div>
            <div class="mb-3 col-12 col-md-6" data-aos="fade-up" data-aos-delay="200">
                <div class="w-75 mx-auto">
                    <label for="lastName" class="form-label text-uppercase fw-bold">Last name <span
                            class="text-danger">*</span></label>
                    <input type="text" class="form-control" id="lastName" name="lastName"
                        placeholder="Enter your last name" v-model="lastName" @blur="v$.lastName.$touch"
                        :class="{'is-invalid': validationStatus(v$.lastName)}">
                    <div v-if="v$.lastName.$error" class="invalid-feedback">Last name field is required</div>
                </div>
            </div>
            <div class="mb-3 col-12 col-md-6" data-aos="fade-up" data-aos-delay="300">
                <div class="w-75 mx-auto">
                    <label for="paymentMode" class="form-label text-uppercase fw-bold">Payment mode <span
                            class="text-danger">*</span></label>
                    <br>
                    <div class="d-flex justify-content-between">
                        <div>
                            <input type="radio" id="paymentMode" name="paymentMode" value="visa"
                                v-model="paymentMode"><span class="ms-2">Visa</span>
                        </div>
                        <div>
                            <input type="radio" id="paymentMode" name="paymentMode" value="mastercard"
                                v-model="paymentMode"><span class="ms-2">Mastercard</span>
                        </div>
                        <div>
                            <input type="radio" id="paymentMode" name="paymentMode" value="amex"
                                v-model="paymentMode"><span class="ms-2">Amex</span>
                        </div>
                    </div>
                </div>
            </div>
            <div class="mb-3 col-12 col-md-6" data-aos="fade-up" data-aos-delay="400">
                <div class="w-75 mx-auto">
                    <label for="company" class="form-label text-uppercase fw-bold">Company<span
                            class="text-danger">*</span></label>
                    <input type="text" class="form-control" id="company" name="company"
                        placeholder="Enter the company you're working at" v-model="company" @blur="v$.company.$touch"
                        :class="{'is-invalid': validationStatus(v$.company)}">
                    <div v-if="v$.company.$error" class="invalid-feedback">Company field is required</div>
                </div>
            </div>
            <div class="mb-3 col-12 col-md-6" data-aos="fade-up" data-aos-delay="500">
                <div class="w-75 mx-auto">
                    <label for="cardNumber" class="form-label text-uppercase fw-bold">Card number <span
                            class="text-danger">*</span></label>
                    <input type="text" class="form-control" id="cardNumber" name="cardNumber"
                        placeholder="Enter your card number" v-model="cardNumber" @blur="v$.cardNumber.$touch"
                        :class="{'is-invalid': validationStatus(v$.cardNumber)}">
                    <div v-if="v$.cardNumber.$error" class="invalid-feedback">Card number field only contains numbers
                    </div>
                </div>
            </div>
            <div class="mb-3 col-12 col-md-6" data-aos="fade-up" data-aos-delay="600">
                <div class="w-75 mx-auto">
                    <label for="email" class="form-label text-uppercase fw-bold">Email <span
                            class="text-danger">*</span></label>
                    <input type="email" class="form-control" id="email" name="email" placeholder="Enter your email"
                        v-model="email" @blur="v$.email.$touch" :class="{'is-invalid': validationStatus(v$.email)}">
                    <div v-if="v$.email.$error" class="invalid-feedback">Invalid email</div>
                </div>
            </div>
            <div class="mb-3 col-12 col-md-6" data-aos="fade-up" data-aos-delay="700">
                <div class="w-75 mx-auto">
                    <label for="expiration" class="form-label text-uppercase fw-bold">Expiration <span
                            class="text-danger">*</span></label>
                    <input type="month" class="form-control" id="expiration" name="expiration"
                        placeholder="Enter your expiration date" v-model="expiration" @blur="v$.expiration.$touch"
                        :class="{'is-invalid': validationStatus(v$.expiration)}">
                    <div v-if="v$.expiration.$error" class="invalid-feedback">Expiration field is required</div>
                </div>
            </div>
            <div class="mb-3 col-12 col-md-6" data-aos="fade-up" data-aos-delay="800">
                <div class="w-75 mx-auto">
                    <label for="phoneNumber" class="form-label text-uppercase fw-bold">Phone Number <span
                            class="text-danger">*</span></label>
                    <input type="tel" class="form-control" id="phoneNumber" name="phoneNumber"
                        placeholder="Enter your phone number" v-model="phoneNumber" @blur="v$.phoneNumber.$touch"
                        :class="{'is-invalid': validationStatus(v$.phoneNumber)}">
                    <div v-if="v$.phoneNumber.$error" class="invalid-feedback">Phone
                        number length must be between 10 and 12 numeric character
                    </div>
                </div>
            </div>
            <div class="mb-3 col-12 col-md-6" data-aos="fade-up" data-aos-delay="900">
                <div class="w-75 mx-auto">
                    <label for="CVN" class="form-label text-uppercase fw-bold">CVN <span
                            class="text-danger">*</span></label>
                    <input type="text" class="form-control" id="CVN" name="CVN" placeholder="Enter your CVN number"
                        v-model="CVN" @blur="v$.CVN.$touch" :class="{'is-invalid': validationStatus(v$.CVN)}">
                    <div v-if="v$.CVN.$error" class="invalid-feedback">CVN field only contains number</div>
                </div>
            </div>
            <div class="mb-4 col-12" data-aos="fade-up" data-aos-delay="1000">
                <div class="donate-bar mx-auto">
                    <label for="donateMoney" class="form-label text-uppercase fw-bold">Donate us<span
                            class="text-danger">*</span></label>
                    <div class="d-flex">
                        <span>0</span>
                        <input name="donateMoney" id="donateMoney" type="range" class="form-range mx-3" min="0"
                            max="1000" v-model="donateMoney" @blur="v$.donateMoney.$touch"
                            :class="{'is-invalid': validationStatus(v$.donateMoney)}">
                        <span>1000</span>
                    </div>
                    <div v-if="v$.donateMoney.$error" class="invalid-feedback">Donate money field only contains number
                    </div>
                </div>
            </div>
            <div class="text-end buttons" data-aos="fade-up" data-aos-delay="1100">
                <button type="submit" class="btn btn-success">SUBMIT</button>
                <button type="reset" class="btn btn-secondary ms-3">RESET</button>
            </div>
        </div>
    </form>
</template>

<script>
import { required, email, numeric, minLength, maxLength } from '@vuelidate/validators'
import useVuelidate from '@vuelidate/core'
export default {
    name: 'DonateForm',
    setup() {
        return {
            v$: useVuelidate()
        }
    },
    data() {
        return {
            firstName: '',
            lastName: '',
            gender: '',
            paymentMode: 'visa',
            company: '',
            cardNumber: '',
            email: '',
            expiration: '',
            phoneNumber: '',
            CVN: '',
            donateMoney: 500
        }
    },
    validations() {
        return {
            firstName: { required },
            gender: { required },
            lastName: { required },
            paymentMode: { required },
            company: { required },
            cardNumber: { required, numeric },
            email: { required, email },
            expiration: { required },
            phoneNumber: { required, numeric, minLength: minLength(10), maxLength: maxLength(12) },
            CVN: { required, numeric },
            donateMoney: { required, numeric }
        }
    },
    methods: {
        handleSubmit: function () {
            this.v$.$touch();
            if (this.v$.$pendding || this.v$.$error) return;
            alert('Data submit successfully')
        },
        validationStatus(validation) {
            return typeof validation != "undefined" ? validation.$error : false
        }
    }
}
</script>

<style lang="scss" scoped>
.form-label {
    font-size: 12px;
}

.donate-bar {
    width: 88%;
}

.buttons {
    width: 94%;

    .btn {
        padding: 10px 35px;
    }
}
</style>