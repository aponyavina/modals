<template>
    <Modal
    title="Second Modal + Validate" 
    @close="$emit('close')"
    >
        <div slot="body">
            <form @submit.prevent="">
                <label>Name:</label>
                <input type="text" required>
                <label>E-mail:</label>
                <input type="email" required>
                <button class="btn btnPrimary">Submit!</button>
            </form>
        </div>
    </Modal>
</template>

<script>
import Modal from '@/components/Modal'
export default {
    components: {
        Modal
    }
}
</script>