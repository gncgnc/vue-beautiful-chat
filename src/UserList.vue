<template>
  <div class="user-list" :style="{background: userListColor.userList.bg, paddingTop: '5px'}">
    <div
      class="user-list--row"
      v-for="user in participants"
      :key="user.id"
      @click.prevent="$emit('chatClicked', user)"
    >
      <img :src="user.imageUrl" class="img-msg" />
      <div class="user-element" :style="{color: userListColor.userList.text}">{{ user.name }}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    participants: {
      type: Array,
      required: true
    },
    colors: {
      type: Object,
      default: () => ({})
    }
  },
  computed: {
    userListColor() {
      const defaultColors = {
        userList: {
          bg: '#FFFFFF',
          text: '#000000'
        }
      }
      return Object.assign(defaultColors, this.colors)
    }
  }
}
</script>

<style scoped>
.user-list {
  height: 100%;
  overflow: auto;
  padding-left: 5px;
  padding-top: 8px;
  border-bottom-left-radius: 11px;
  border-bottom-right-radius: 11px;
}
.img-msg {
  border-radius: 50%;
  width: 50px;
  margin-right: 5px;
}
.user-element {
  font-size: 20px;
  vertical-align: middle;
}

.user-list--row {
  cursor: pointer;
  display: flex;
  align-items: center;
  padding: 10px;
  border-radius: 10px;
  margin: 5px;
}

.user-list--row:hover {
  background: rgb(68, 61, 61);
}
</style>
