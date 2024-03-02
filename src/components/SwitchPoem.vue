<template>
  <div class="container">
    <div class="dots">
      <div v-for="items in poemsData" :key="items.id" :class="{active: !isExistItem(items.id)}" @click="checkItem(items.id)"></div>
    </div>
    <div class="poem">
      <h1 class="title">Lorem</h1>
      <div class="poem__items">
        <div v-for="items in poemsData" :key="items.id" v-show="isExistItem(items.id)">
          {{ items.text }}
        </div>
      </div>
    </div>
    <div class="author">By Lorem</div>
  </div>
</template>

<script>
export default {
  name: 'SwitchPoem',
  data() {
    return {
      activeId: [],
      poemsData: [
        {
          id: 0,
          text: "1 Lorem ipsum dolor sit, amet consectetur adipisicing elit. Sunt perferendis perspiciatis iusto unde nobis exercitationem distinctio, ex deleniti dignissimos, velit architecto voluptatem ab blanditiis facilis possimus vitae eius sequi ipsum!"
        },
        {
          id: 1,
          text: "2 Lorem ipsum dolor sit, amet consectetur adipisicing elit. Sunt perferendis perspiciatis iusto unde nobis exercitationem distinctio, ex deleniti dignissimos, velit architecto voluptatem ab blanditiis facilis possimus vitae eius sequi ipsum!"
        },
        {
          id: 2,
          text: "3 Lorem ipsum dolor sit, amet consectetur adipisicing elit. Sunt perferendis perspiciatis iusto unde nobis exercitationem distinctio, ex deleniti dignissimos, velit architecto voluptatem ab blanditiis facilis possimus vitae eius sequi ipsum!"
        },
        {
          id: 3,
          text: "4 Lorem ipsum dolor sit, amet consectetur adipisicing elit. Sunt perferendis perspiciatis iusto unde nobis exercitationem distinctio, ex deleniti dignissimos, velit architecto voluptatem ab blanditiis facilis possimus vitae eius sequi ipsum!"
        }
      ]
    }
  },
  methods: {
    checkItem(id) {
      if (this.activeId.indexOf(id) === -1) {
        if (this.activeId.length >= 3) return;

        this.activeId.push(id);
      } else {
        this.activeId.splice(this.activeId.indexOf(id), 1);
      }
    },
    isExistItem(id) {
      if (this.activeId.indexOf(id) !== -1) {
        return false;
      } else {
        return true;
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.title {
  text-align: center;
  margin-top: 0;
}

.container {
  display: flex;
  gap: 40px;
  max-width: 1000px;
  width: 100%;
  margin: 0 auto;
}

.dots {
  display: flex;
  justify-content: center;
  gap: 5px;
  margin-top: 20px;
  
  div {
    width: 15px;
    height: 15px;
    background: #000;
    cursor: pointer;
    border: 1px solid transparent;

    &.active {
      border: 1px solid #000;
      background: none;
    }
  }
}

.poem {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 60%;

  &__items {
    display: flex;
    flex-direction: column;
    gap: 30px;
  }
}

.author {
  display: flex;
  justify-content: flex-start;
  width: 30%;
  margin-top: 20px;
}
</style>
