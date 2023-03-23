<!-- table component -->
<template>
  <!-- table has props column and data -->
  <a-table :columns="columns" :data-source="data">

    <!-- table header cell component -->
    <template #headerCell="{ column }">
      <template v-if="column.key === 'country'">
        <span>
          Country
        </span>
      </template>
    </template>

    <!-- table body cell component -->
    <template #bodyCell="{ column, record }">
      <!-- checks for user danger status (danger attribute) to set the colour accordingly -->
      <template v-if="column.key === 'danger'">
        <span>
          <a-tag
            v-for="tag in record.danger"
            :key="tag"
            :color="tag === 'High Risk' ? 'red'
            : tag === 'Moderate Risk' ? 'orange' : 'green'"
          >
            {{ tag.toUpperCase() }}
          </a-tag>
        </span>
      </template>
    </template>
  </a-table>
</template>
<script lang="ts">
import { DownOutlined } from '@ant-design/icons-vue';
import { defineComponent } from 'vue';

const columns = [
  {
    country: 'country',
    dataIndex: 'country',
    key: 'country',
  },
  {
    title: 'Disaster Type',
    dataIndex: 'disaster',
    key: 'disaster',
  },
  {
    title: 'Distance Away (km)',
    dataIndex: 'distance',
    key: 'distance',
  },
  {
    title: 'Time of incidence',
    dataIndex: 'incidence',
    key: 'incidence',
  },
  {
    title: 'Danger Status',
    key: 'danger',
    dataIndex: 'danger',
  },
];

// to pull from API
const data = [
  {
    key: '1',
    country: 'Chile',
    disaster: 'Earthquake',
    distance: '1.0km',
    incidence: "Thu, 23 Feb 2023 20:20:21 GMT",
    danger: ['Low Risk'],
  },
  {
    key: '2',
    country: 'Cuba',
    disaster: 'Earthquake',
    distance: '5.0km',
    incidence: "Thu, 23 Feb 2023 10:39:01 GMT",
    danger: ['High Risk'],
  },
  {
    key: '3',
    country: 'Turkey',
    disaster: 'Earthquake',
    distance: '10.0km',
    incidence: "Thu, 23 Feb 2023 00:54:02 GMT",
    danger: ['Moderate Risk'],
  },
  {
    key: '4',
    country: 'Korea',
    disaster: 'Fire',
    distance: '10.0km',
    incidence: "Thu, 23 Feb 2023 00:54:02 GMT",
    danger: ['Low Risk'],
  },
];

export default defineComponent({
  components: {
    DownOutlined,
  },
  setup() {
    return {
      data,
      columns,
    };
  },
});
</script>
