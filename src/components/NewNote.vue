<template>
  <div class="new-note">
    <label>Title</label>
    <div class="imp">
 <input v-model="note.title" type="text" />
    <select name="user_profile_color_2" class="select">
  <option value="">Выберите приоритет</option>
  <option value="1">Стандартный</option>
  <option value="2" style="color:gold">Важный</option>
  <option value="3" style="color:red">Очень важный</option>
</select>
    </div>
   
    <label>Description</label>
    <textarea v-model="note.descr"></textarea>
    <button style="margin: 36px 0;" class="btn btnPrimary" @click="addNote">New note</button>
  </div>
</template>

<script>
export default {
    props: {
        note: {
            type: Object,
            required: true
        }
    },
    methods: {
        addNote () {
            this.$emit('addNote', this.note);
        }
    }
}
</script>

<style lang="scss">
    .new-note {
        text-align: center;;
    }

    .imp {
        display: flex;
    }

    .select {
        height: 57px;
        border-radius: 50px;
        cursor: pointer;
    }

   
</style>