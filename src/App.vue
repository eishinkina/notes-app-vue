<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <!-- title -->
          <h1>{{ title }}</h1>
          <!-- message -->
          <Message v-if="message" :message="message" />
          <!-- new notes -->
          <NewNote :note="note" @addNote="addNote" />
          <!-- note list  -->
          <Notes :notes="notes" @remove="removeNote"/>
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

<style></style>
