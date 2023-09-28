<template>
    <div class="notes">
        <div class="note" :class="{ full: !grid }" v-for="(note, i) in notes" :key="i">
            <div class="note-header">
                <p>{{ note.title }}</p>
                <p style="cursor: pointer;" @click="removeNote(i)">x</p>
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
        },
        grid: {
            type: Boolean,
            require: true
        }
    },
    methods: {
        removeNote(i) {
            console.log(`note ${i} Id = removed`)
            this.$emit('remove', i)
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
    transition: all.025s cubic-bezier(.02, .01, .47, 1);
    box-shadow: 0 30px 30px rgba(0, 0, 0, .02);

    &.full {
        width: 100%;
    }

    &:hover {
        box-shadow: 0 30px 30px rgba(0, 0, 0, .04);
        transform: translate(0, -6px);
        transition-delay: 0s !important;
    }

}

.note-header {
    display: flex;
    align-items: center;
    justify-content: space-between;

    p {
        color: #281da3;

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