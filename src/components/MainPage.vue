<template>
  <div class="main-page">
    <div class="left-menu" @click.self="onEditNoteEnd()">
       <!-- ノートリスト -->
       <div class="note" v-for="note in noteList" v-bind:key="note.id">
        <div class="note-icon">
          <i class="fas fa-file-alt"></i>
        </div>
        <div class="note-name">{{note.name}}</div>
        <div class="button-icon" @click="onClickDelete(note)">
        <i class="fas fa-trash"></i>
      </div>
      </div>
      <!-- ノート追加ボタン -->
      <button class="transparent" @click="onClickButtonAdd">
        <i class="fas fa-plus-square"></i>ノートを追加
      </button>
    </div>
    <div class="right-view" @click.self="onEditNoteEnd()">
      右ビュー
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      noteList : [],
    }
  },
  methods: {
    onClickButtonAdd : function() {
      this.noteList.push({
        id : new Date().getTime().toString(16),
        name : `新規ノート`,
      })
    },
    onClickDelete : function(deleteNote) {
      const index = this.noteList.indexOf(deleteNote);
      this.noteList.splice(index, 1);
    },
    onEditNoteStart : function(editNote) {
      for (let note of this.noteList) {
        note.editing = (note.id === editNote.id);
      }
    },
    onEditNoteEnd : function() {
      for (let note of this.noteList) {
          note.editing = false;
      }
    },
  },
}
</script>

<style scoped>
.main-page {
  display: flex;
  height: calc(100vh - 60px);
}

.left-menu {
  width: 350px;
  background-color: #f7f6f3;
}

.note {
      margin: 10px 0;
      display: flex;
      align-items: center;
      padding: 5px;
      color: rgba(25, 23, 17, 0.6);
      .note-icon {
        margin-left: 10px;
      }
      .note-name {
        width: 100%;
        padding: 3px 10px;
      }
    }
.right-view {
  flex-grow: 1;
  padding: 10px;
}

</style>
