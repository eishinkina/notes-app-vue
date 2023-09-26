<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <h1>{{ title }}</h1>
          <div class="message" v-if="message">
            <p>{{ message }}</p>
          </div>
          <!-- new notes -->
          <div class="new-note">
            <input v-model="note.title" type="text" />
            <textarea v-model="note.descr"></textarea>
            <button @click="addNote">New note</button>
          </div>
          <!-- note list  -->
          <div class="notes">
            <div class="note" v-for="(note, i) in notes" :key="i">
              <div class="note-header">
                <h3>{{ note.title }}</h3>
              </div>
              <div class="note-body">
                <p>{{ note.descr }}</p>
              </div>
              <span>{{ note.data }}</span>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
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
  },
}
</script>

<style></style>
