<template>
  <div class="notes">
    <div class="note" :class="{full: !grid}" v-for="(note, index) in notes" :key="index" :style="`background-color: ${getColor(note.status)} ;`">
      <div class="note-header" :class="{full: !grid}">
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
        },
        getColor(status) {
            if(status === '0') {
                return 'white' 
            }else if (status === '1') {
                return 'gold'
            }else {
                return 'red'
            }
            
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
    transition: all .25s cubic-bezier(0.2,.01,.47,1);
    box-shadow: 0 30px 30px rgba(0, 0, 0,.02);
    &:hover {
         box-shadow: 0 30px 30px rgba(0, 0, 0,.04);
         transform: translate(0,-6px);
         transition-delay: 0s !important;
    }
    &.full {
        width: 100%;
    }
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