<template>
  <div>
    <Nav :nav="nav" @onNav="changeNav" />
    <div v-if="nav === 1">
      <button
        class="btn btn-dark"
        style="float: right; margin: -50px 50px 0 0"
        @click="onToggleModal"
      >
        Add Card
      </button>
      <div class="card-list">
        <Card
          v-for="card in cards"
          :key="card.id"
          class="card-item"
          :id="card.id"
          @deleteCard="deleteCard"
        >
          <template v-slot:name>
            {{ card.name }}
          </template>
          <template v-slot:title>
            {{ card.title }}
          </template>
          <template v-slot:description>
            {{ card.description }}
          </template>
        </Card>
      </div>
      <Modal
        @closeModal="onToggleModal"
        @addCart="addCart"
        v-if="isShowModal"
      ></Modal>
    </div>
  </div>
</template>

<script>
import Nav from "./components/Nav.vue";
import Card from "./components/Card.vue";
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: {
    Nav,
    Card,
    Modal,
  },
  data() {
    return {
      isShowModal: false,
      cards: [
        {
          id: 1,
          name: "Card 1",
          title: "Title 1",
          description:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium possimus ut commodi consectetur ullam sequi fuga voluptatem ratione aliquid iusto!",
        },
        {
          id: 2,
          name: "Card 2",
          title: "Title 2",
          description:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium possimus ut commodi consectetur ullam sequi fuga voluptatem ratione aliquid iusto!",
        },
        {
          id: 3,
          name: "Card 3",
          title: "Title 3",
          description:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium possimus ut commodi consectetur ullam sequi fuga voluptatem ratione aliquid iusto!",
        },
      ],
      nav: 1,
    };
  },
  methods: {
    onToggleModal() {
      this.isShowModal = !this.isShowModal;
    },
    addCart(name, title, description) {
      this.cards = [
        ...this.cards,
        {
          id: this.cards.length + 1,
          name: name,
          title: title,
          description: description,
        },
      ];
    },
    deleteCard(id) {
      this.cards = this.cards.filter((card) => card.id !== id);
    },
    changeNav(id) {
      this.nav = id;
      console.log(this.nav);
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.card {
  &-list {
    margin: 70px 50px 50px;
    display: flex;
    flex-wrap: wrap;
  }
  &-item {
    margin-bottom: 15px;
    margin-right: 15px;
    max-width: calc(25% - 11.25px);
    &:nth-child(4n) {
      margin-right: 0;
    }
  }
}
</style>
