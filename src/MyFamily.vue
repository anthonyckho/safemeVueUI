<template>
  <div class="card-list">
    <a-row :gutter="16">
      <a-col :span="6" v-for="(card, index) in cards" :key="index">
        <a-card :hoverable="true" :body-style="{ padding: '12px 24px' }">
          <a-card-meta :title="card.name" :description="card.email" />
          <a-image :src="card.image" :alt="card.name" :height="200" />
          <template slot="extra">
            <a-tag :color="card.status === 'Active' ? 'green' : 'red'">{{ card.status }}</a-tag>
          </template>
        </a-card>
      </a-col>
    </a-row>
  </div>
</template>

<script>
import { Row, Col, Card, CardMeta, Image, Tag } from "ant-design-vue";

export default {
  name: "CardList",
  components: { "a-row": Row, "a-col": Col, "a-card": Card, "a-card-meta": CardMeta, "a-image": Image, "a-tag": Tag },
  data() {
    return {
      cards: [
        {
          name: "John Smith",
          image: "https://via.placeholder.com/200x300",
          status: "Active",
          email: "john.smith@example.com",
        },
        {
          name: "Jane Doe",
          image: "https://via.placeholder.com/200x300",
          status: "Inactive",
          email: "jane.doe@example.com",
        },
        // Add more cards here...
      ],
    };
  },
};
</script>

<style>
.card-list {
  margin: 24px 0;
}
</style>
