<template>
    <div class="new-note">
        <label for="">Title</label>
        <input v-model="note.title" type="text" />
        <label for="">Description</label>
        <textarea v-model="note.descr"></textarea>
        <button class="btn btnPrimary" @click="addNote">New note</button>
    </div>
</template>

<script>
export default {
    props: {
        note: {
            type: Object,
            require: true,
        }
    },
    methods: {
        addNote() {
            this.$emit('addNote', this.note)
        }
    }

}
</script>

<style lang="scss" scoped>
textarea {
    margin-bottom: 20px;
}
.new-note {
    text-align: center;
    margin-bottom: 20px;
}
</style>