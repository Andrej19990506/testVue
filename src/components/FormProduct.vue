<template >
    <div class="page__form">
        <div class="form-product">
            <transition name="alert-fade">
                <AlertModal v-if="alertTreggers.modalShow" :toogleAlert="() => toogleAlert('modalShow')">Товар успешно
                    добавлен
                </AlertModal>
            </transition>
            <p v-if="alertTreggers.modalShow == false" class="title" style="text-align:center">Добовить товара</p>
            <form class="form" v-on:submit.prevent novalidate>
                <span v-if="v$.product.name.$error" class="form__title-error">
                    Введите название товара
                    <svg width="15px" height="15px" viewBox="0 0 24 24" fill="white" xmlns="http://www.w3.org/2000/svg">
                        <g id="Iconly/Curved/Danger Square">
                            <g id="Danger Circle">
                                <path id="Stroke 1" fill-rule="red" clip-rule="evenodd"
                                    d="M2.74976 12C2.74976 5.063 5.06276 2.75 11.9998 2.75C18.9368 2.75 21.2498 5.063 21.2498 12C21.2498 18.937 18.9368 21.25 11.9998 21.25C5.06276 21.25 2.74976 18.937 2.74976 12Z"
                                    stroke="red" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
                                <path id="Stroke 3" d="M11.9998 8.10498V12" stroke="red" stroke-width="1.5"
                                    stroke-linecap="round" stroke-linejoin="round" />
                                <path id="Stroke 15" d="M11.9955 15.5H12.0045" stroke="red" stroke-width="1.5"
                                    stroke-linecap="round" stroke-linejoin="round" />
                            </g>
                        </g>
                    </svg>
                </span>
                <span v-else class="form__title">Название товара</span>
                <input class="form__name form__input" @blur="v$.product.name.$touch()" v-bind:class="{
                    invalid:
                        v$.product.name.$error
                }" v-model="product.name" type="text"
                    placeholder="Введите наименование товара" />
                <span class="form__title">Описание товара</span>
                <textarea class="form__discription form__input" v-model="product.discription"
                    placeholder="Введите описание товара" />
                <span v-if="v$.product.sourse.url.$invalid" class="form__title-error">
                    URL не корректен
                    <svg width="15px" height="15px" viewBox="0 0 24 24" fill="white" xmlns="http://www.w3.org/2000/svg">
                        <g id="Iconly/Curved/Danger Square">
                            <g id="Danger Circle">
                                <path id="Stroke 1" fill-rule="red" clip-rule="evenodd"
                                    d="M2.74976 12C2.74976 5.063 5.06276 2.75 11.9998 2.75C18.9368 2.75 21.2498 5.063 21.2498 12C21.2498 18.937 18.9368 21.25 11.9998 21.25C5.06276 21.25 2.74976 18.937 2.74976 12Z"
                                    stroke="red" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
                                <path id="Stroke 3" d="M11.9998 8.10498V12" stroke="red" stroke-width="1.5"
                                    stroke-linecap="round" stroke-linejoin="round" />
                                <path id="Stroke 15" d="M11.9955 15.5H12.0045" stroke="red" stroke-width="1.5"
                                    stroke-linecap="round" stroke-linejoin="round" />
                            </g>
                        </g>
                    </svg>
                </span>
                <span v-else-if="v$.product.sourse.$error" class="form__title-error">
                    Введите сылку
                    <svg width="15px" height="15px" viewBox="0 0 24 24" fill="white" xmlns="http://www.w3.org/2000/svg">
                        <g id="Iconly/Curved/Danger Square">
                            <g id="Danger Circle">
                                <path id="Stroke 1" fill-rule="red" clip-rule="evenodd"
                                    d="M2.74976 12C2.74976 5.063 5.06276 2.75 11.9998 2.75C18.9368 2.75 21.2498 5.063 21.2498 12C21.2498 18.937 18.9368 21.25 11.9998 21.25C5.06276 21.25 2.74976 18.937 2.74976 12Z"
                                    stroke="red" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
                                <path id="Stroke 3" d="M11.9998 8.10498V12" stroke="red" stroke-width="1.5"
                                    stroke-linecap="round" stroke-linejoin="round" />
                                <path id="Stroke 15" d="M11.9955 15.5H12.0045" stroke="red" stroke-width="1.5"
                                    stroke-linecap="round" stroke-linejoin="round" />
                            </g>
                        </g>
                    </svg>
                </span>
                <span v-else class="form__title">
                    Сылка на изображение товара
                </span>
                <input class="form__sourse form__input" @blur="v$.product.sourse.$touch()" v-bind:class="{
                    invalid:
                        v$.product.sourse.$error
                }" v-model="product.sourse" type="text" placeholder=" Введите сылку" />
                <span v-if="v$.product.price.$error" class="form__title-error">
                    Введите цену
                    <svg width="15px" height="15px" viewBox="0 0 24 24" fill="white" xmlns="http://www.w3.org/2000/svg">
                        <g id="Iconly/Curved/Danger Square">
                            <g id="Danger Circle">
                                <path id="Stroke 1" fill-rule="red" clip-rule="evenodd"
                                    d="M2.74976 12C2.74976 5.063 5.06276 2.75 11.9998 2.75C18.9368 2.75 21.2498 5.063 21.2498 12C21.2498 18.937 18.9368 21.25 11.9998 21.25C5.06276 21.25 2.74976 18.937 2.74976 12Z"
                                    stroke="red" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
                                <path id="Stroke 3" d="M11.9998 8.10498V12" stroke="red" stroke-width="1.5"
                                    stroke-linecap="round" stroke-linejoin="round" />
                                <path id="Stroke 15" d="M11.9955 15.5H12.0045" stroke="red" stroke-width="1.5"
                                    stroke-linecap="round" stroke-linejoin="round" />
                            </g>
                        </g>
                    </svg>
                </span>
                <span v-else class="form__title">Цена товара</span>
                <input class="form__price form__input" @blur="v$.product.price.$touch()"
                    v-bind:class="{ invalid: v$.product.price.$error }" v-model="product.price" type="text"
                    placeholder="Введите цену" />
                <button v-bind:class="{ disabledBtn: v$.product.$invalid, button: !v$.product.$invalid }"
                    :disabled="disabledBtn" @click="createProduct">Добавить товар</button>
            </form>
        </div>
    </div>
</template>
<script>
import AlertModal from './AlertModal.vue';
import useVuelidate from '@vuelidate/core'
import { required, url } from '@vuelidate/validators'
import { ref } from 'vue';

export default {
    components: { AlertModal },
    setup() {

        const toogleAlert = (toggle) => {
            alertTreggers.value[toggle] = !alertTreggers.value[toggle]
        };

        const alertTreggers = ref({
            modalShow: false
        });


        return {
            v$: useVuelidate(),
            alertTreggers,
            toogleAlert
        }



    },



    data() {
        return {
            product: {
                name: '',
                discription: '',
                sourse: '',
                price: ''
            },

        }
    },
    validations() {
        return {
            product: {
                name: { required },
                sourse: { required, url },
                price: { required }
            }
        }
    },
    computed: {
        disabledBtn() {
            return this.v$.product.name.$invalid ||
                this.v$.product.sourse.$invalid ||
                this.v$.product.price.$invalid
        }



    },

    methods: {
        createProduct() {
            this.product.id = Date.now();
            this.$emit('create', this.product);
            this.product = {
                name: '',
                discription: '',
                sourse: '',
                price: ''
            }
            this.alertTreggers.modalShow = true;
            this.removeAlert()
            console.log(this.products.id)
        },

        removeAlert() {
            this.alertTreggers.modalShow = setTimeout(() => {
                this.alertTreggers.modalShow = false;
            }, 3000)
        }

    }
}
</script>



<style lang="scss">

@import '../assets/style.scss';

.alert-fade-enter-active {
    transition: all 0.2s ease-out;
}

.alert-fade-leave-active {
    transition: all 0.6s cubic-bezier(1, 0.5, 0.8, 1);
}

.alert-fade-enter-from {
    transform: translateY(-40px);
}

.alert-fade-leave-to {
    transform: translateY(-40px);
    opacity: 0;
}

.invalid:focus {
    animation-name: bounce-6;
    animation-duration: 600ms;
    animation-timing-function: ease;
    animation-direction: alternate;
    animation-iteration-count: 1;
    outline: 1px solid red !important;

}

@keyframes bounce-6 {
    0% {
        transform: scale(1.0, 1.0) translateX(0px);
    }

    15% {
        transform: scale(1.0, 1.0) translateX(5px);
    }

    30% {
        transform: scale(1.0, 1.0) translateX(-5px);
    }

    45% {
        transform: scale(1.0, 1.0) translateX(5px);
    }

    60% {
        transform: scale(1.0, 1.0) translateX(-5px);
    }

    75% {
        transform: scale(1.0, 1.0) translateX(5px);
    }

    90% {
        transform: scale(1.0, 1.0) translateX(-5px);
    }


    100% {
        transform: scale(1.0, 1.0) translateX(0px);
    }
}

.invalid {
    outline: 1px solid red !important;
}

.disabledBtn {
    background: #EEEEEE;
    border-radius: 10px;
    border: none;
    font-family: 'Inter';
    font-style: normal;
    font-weight: 600;
    font-size: 12px;
    line-height: 15px;
    text-align: center;
    letter-spacing: -0.02em;
    color: #B4B4B4;
    padding: 10px 0 10px 0;
}

.page__form {
    max-width: 415px;
    width: 100%;
    display: flex;
    justify-content: center;
    border-right: 1px solid;
    background: oldlace;
}

.form-product {
    display: flex;
    flex-direction: column;
    max-width: 332px;
    width: 100%;
    justify-content: center;
}

.button {
    background: #7BAE73;
    box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
    border-radius: 10px;
    border: none;
    font-family: 'Inter';
    font-style: normal;
    font-weight: 600;
    font-size: 12px;
    line-height: 15px;
    text-align: center;
    letter-spacing: -0.02em;
    color: white;
    padding: 10px 0 10px 0;
    cursor: pointer;

}

.form {
    margin-top: 16px;
    padding: 24px;
    display: flex;
    flex-direction: column;
    background: #FFFEFB;
    box-shadow: 0px 10px 12px rgb(0 0 0);
    border-radius: 20px;
    outline: 1px solid black;

    textarea::placeholder {
        font-family: 'Source Sans Pro';
        font-style: normal;
        font-weight: 400;
        font-size: 12px;
        line-height: 15px;
        color: #B4B4B4;
    }

    input::-webkit-input-placeholder {
        font-family: 'Source Sans Pro';
        font-style: normal;
        font-weight: 400;
        font-size: 12px;
        line-height: 15px;
        color: #B4B4B4;
    }

    input:focus {
        outline: none;
    }

    textarea:focus {
        outline: none
    }
    &__discription{
        -webkit-appearance: none;
            resize: none
    }
    &__input {
        padding: 10px 0 10px 16px;
        background: #FFFEFB;
        box-shadow: 0px 4px 7px rgba(0, 0, 0, 0.1);
        border-radius: 4px;
        font-family: 'Source Sans Pro';
        font-style: normal;
        font-weight: 400;
        font-size: 16px;
        line-height: 15px;
        color: black;
        margin-bottom: 16px;
        border: none;
        position: relative;
        cursor: pointer;
    }

    &__input:hover {
        box-shadow: 0px 1px 3px rgba(0, 0, 0, 0.1);
    }


    &__input:nth-child(4) {
        min-height: 108px;
    }

    &__input:nth-child(4) {
        margin-bottom: 24px;
    }

    &__title {
        font-family: 'Source Sans Pro';
        font-style: normal;
        font-weight: 400;
        font-size: 10px;
        line-height: 13px;
        letter-spacing: -0.02em;
        color: #49485E;
        margin-bottom: 4px;
        position: relative;
    }

    &__title-error {
        font-family: 'Source Sans Pro';
        font-style: normal;
        font-weight: 400;
        font-size: 12px;
        line-height: 13px;
        letter-spacing: -0.02em;
        color: red;
        margin-bottom: 4px;
    }

    &__title:nth-child(1)::before {
        content: "*";
        display: block;
        color: red;
        position: absolute;
        left: 71px;
        top: 0;
        font-size: 14px;
    }

    &__title:nth-child(5)::before {
        content: "*";
        display: block;
        color: red;
        position: absolute;
        left: 126px;
        top: 0px;
        font-size: 14px;
    }

    &__title:nth-child(7)::before {
        content: "*";
        content: "*";
        display: block;
        color: red;
        position: absolute;
        left: 53px;
        top: 0px;
        font-size: 14px;
    }
}

.title {
    left: 88px;
    text-align: center;
    font-family: 'Source Sans Pro';
    font-style: normal;
    font-weight: 600;
    font-size: 28px;
    line-height: 35px;
    color: #3F3F3F;
    position: fixed;
    top: 30px;
}
</style>