<template>
  <div class="notes">
    <div class="note" v-for="(note, index) in notes" :key="index">
      <div class="note-header">
        <p>{{ note.title }}</p>
        <p style="cursor:pointer" @click="removeNote(index)">x</p>
      </div>
      <div class="note-body">
        <p>{{ note.descr }}</p>
        <span>{{ note.date }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    props: {
        notes: {
            type: Array,
            required: true,
        },
        grid: {
            type: Boolean,
            required: true,
        },
    },
    methods: {
        removeNote (index) {
            this.$emit('remove', index)
        }
    }
}
</script>

<style lang="scss">
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
    display: flex;
    align-items: center;
    justify-content: space-between;
    h1 {
        font-size: 32px;
    }
    p {
        font-size: 22px;
        color: rgb(77, 141, 167);
    }
    svg {
        margin-right: 12px;
        color: #999;
        &.active {
        color: rgb(77, 141, 167);
        }
        &:last-child {
            margin-right: 0;
        }
    }
 }
 .note-body {
    p {
        margin: 20px 0;
    }
    span {
        font-size: 14px;
        color: #999;
    }
 }
</style>