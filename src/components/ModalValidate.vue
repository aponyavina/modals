<template>
    <Modal
    title="Second Modal + Validate" 
    @close="$emit('close')"
    >
        <div slot="body">
            <form @submit.prevent="">
                <div class="form-item" :class="{errorInput: $v.name.$error}">
                    <label>Name:</label>
                    <p class="errorText" v-if="!$v.name.required">Filled is required</p>
                    <p class="errorText" v-if="!$v.name.minLength">Name must have at least {{$v.name.$params.minLength.min}}!</p>
                    <input 
                    v-model="name" 
                    :class="{error: $v.name.$error}"
                    @change="$v.name.$touch()"
                    >
                </div>
                <label>E-mail:</label>
                <input v-model="email">
                <button class="btn btnPrimary">Submit!</button>
            </form>
        </div>
    </Modal>
</template>

<script>
import { required, minLength, email } from 'vuelidate/lib/validators'

import Modal from '@/components/Modal'
export default {
    components: {
        Modal
    },
    data() {
        return {
            name: '',
            email: ''
        }
    },
    validations: {
        name: {
            required,
            minLength: minLength(4)
        },
        email: {
            required,
            email
        }
        
    }
}
</script>

<style lang="scss">
.form-item .errorText {
    display: none;
    margin-bottom: 8px;
    font-size: 13.4px;
    color: #dd5c5c;
}

.form-item {
    &.errorInput .errorText {
        display: block;
    }
}

input.error {
    border-color: #dd5c5c;
}

</style>