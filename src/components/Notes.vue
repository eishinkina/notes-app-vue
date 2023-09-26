<template>
    <div class="notes">
        <div class="note" v-for="(note, i) in notes" :key="i">
            <div class="note-header">
                <p>{{ note.title }}</p>
            </div>
            <div class="note-body">
                <p>{{ note.descr }}</p>
            </div>
            <span>{{ note.data }}</span>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        notes: {
            type: Array,
            require: true
        }
    }

}
</script>

<style lang="scss" scoped>
.notes {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    padding: 40px 0;
}

.note {
    width: 48%;
    padding: 18px 20px;
    margin-bottom: 20px;
    background-color: #fff;
}
.note-header {
   p {
        color: #281da3
    }
}

.note-body {
    p {
        margin: 20px 0;
    }
}

span {
    font-size: 14px;
    color: #999999;
}

</style>