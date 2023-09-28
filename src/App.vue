<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <!-- message -->
          <Message v-if="message" :message="message" />
          <!-- new notes -->
          <NewNote :note="note" @addNote="addNote" />
          <div class="note-header">
            <h1>{{ title }}</h1>
            <div class="icons">
              <svg :class="{ active: grid }" @click="grid = true" style="cursor: pointer;" xmlns="http://www.w3.org/2000/svg" width="24"
                height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"
                stroke-linejoin="round">
                <rect x="3" y="3" width="7" height="7"></rect>
                <rect x="14" y="3" width="7" height="7"></rect>
                <rect x="14" y="14" width="7" height="7"></rect>
                <rect x="3" y="14" width="7" height="7"></rect>
              </svg>
              <svg :class="{ active: !grid }" @click="grid = false" style="cursor: pointer;" xmlns="http://www.w3.org/2000/svg" width="24"
                height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"
                stroke-linejoin="round">
                <line x1="8" y1="6" x2="21" y2="6"></line>
                <line x1="8" y1="12" x2="21" y2="12"></line>
                <line x1="8" y1="18" x2="21" y2="18"></line>
                <line x1="3" y1="6" x2="3" y2="6"></line>
                <line x1="3" y1="12" x2="3" y2="12"></line>
                <line x1="3" y1="18" x2="3" y2="18"></line>
              </svg>
            </div>
          </div>
          <!-- note list  -->
          <Notes :notes="notes" @remove="removeNote" :grid="grid" />
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import Message from './components/Message.vue';
import NewNote from './components/NewNote.vue';
import Notes from './components/Notes.vue';
export default {
  components: {
    Message,
    NewNote,
    Notes
  },
  data() {
    return {
      title: "Notes App",
      message: null,
      grid: true,
      note: {
        title: "",
        descr: "",
      },
      notes: [
        {
          title: "first notes",
          descr: "description for first notes",
          data: new Date(Date.now()).toLocaleString(),
        },
        {
          title: "second notes",
          descr: "description for second notes",
          data: new Date(Date.now()).toLocaleString(),
        },
        {
          title: "thirds notes",
          descr: "description for thirds notes",
          data: new Date(Date.now()).toLocaleString(),
        },
      ],
    }
  },
  methods: {
    addNote() {
      let { title, descr } = this.note;
      if (title === "") {
        this.message = "title can`t be blank!";
        return false;
      }
      this.notes.push({
        title,
        descr,
        data: new Date(Date.now()).toLocaleString(),
      });
      this.message = null;
      this.note.title = "";
      this.note.descr = "";
    },
    removeNote(i) {
      this.notes.splice(i, 1)
    }
  },
}
</script>

<style lang="scss" scoped>
.note-header {
  display: flex;
  align-items: center;
  justify-content: space-between;

  h1 {
    font-size: 32px;
  }

  svg {
    margin-right: 12px;
    color: rgb(174, 169, 169);

    &.active {
      color: #402caf
    }

    &:last-child {
      margin-right: 0;
    }
  }
}
</style>