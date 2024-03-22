<template>
  <div class="main-page">
    <div class="left-menu">
      <!-- ノートリスト -->
      <div class="note" v-for="note in noteList" v-bind:key="note.id">
        <div class="note-icon">
          <i class="fas fa-file-alt"></i>
        </div>
        <div class="note-name">{{ note.name }}</div>
        <div class="button-icon">
          <i class="fas fa-edit"></i>
        </div>
        <div class="button-icon" @click="onDeleteNote">
          <i class="fas fa-trash"></i>
        </div>
      </div>
      <!-- ノート追加ボタン -->
      <button class="transparent" @click="onClickButtonAdd">
        <i class="fas fa-plus-square"></i>ノートを追加
      </button>
    </div>
    <div class="right-view">
      右ビュー
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      noteList: [],
    }
  },
  methods: {
    onClickButtonAdd: function () {
      this.noteList.push({
        id: new Date().getTime().toString(16),
        name: `新規ノート`,
      })
    },

    onDeleteNote: function (deleteNote) {
      const index = this.noteList.indexOf(deleteNote);
      this.noteList.splice(index, 1);
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


.buttons {
  display: flex;
  flex-direction: row;
}

.button-icon {
  padding: 3px;
  margin-left: 3px;
  border-radius: 5px;
}
</style>
