<template>
  <div class="note">
    <div class="note-icon">
      <i class="fas fa-file-alt"></i>
    </div>
    <div class="note-name">{{note.name}}</div>
  </div>
  <div class="button-icon">
        <i class="fas fa-sitemap"></i>
      </div>
      <div class="button-icon">
        <i class="fas fa-plus-circle"></i>
      </div>
      <div class="button-icon">
        <i class="fas fa-edit"></i>
      </div>
      <div class="button-icon">
      <div class="button-icon" @click="onClickDelete(note)">
        <i class="fas fa-trash"></i>
      </div>
    </div>
</template>

<script>
export default {
  name: 'NoteItem',
  props: [
    'note',
  ],
}
</script>

<style scoped lang="scss">
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
</style>
