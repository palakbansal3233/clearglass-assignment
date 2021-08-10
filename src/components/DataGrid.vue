<template>
  <div>
    <h1>Clearglass Assignment</h1>
    <h6 class="my-5">Users {{ value }} selected out of 6</h6>
    <b-table
      selectable
      bordered
      :items="items"
      :fields="fields"
      :sort-by.sync="sortBy"
      :sort-desc.sync="sortDesc"
      responsive="sm">
      <template #cell(select_row)>
        <b-form-checkbox v-model="value" @click="increaseVal"></b-form-checkbox>
      </template>
      <template #cell(actions)>
        <b-icon-pencil-square class="action-icon" />
        <b-icon-eye class="action-icon" />
        <b-icon-trash />
      </template>
    </b-table>
  </div>
</template>

<script>
import { BIconPencilSquare, BIconEye, BIconTrash } from 'bootstrap-vue'

export default {
  data () {
    return {
      value: 0,
      dataResizable: false,
      sortBy: 'id',
      sortDesc: false,
      fields: [
        { key: 'select_row' },
        { key: 'id', sortable: true },
        { key: 'name'},
        { key: 'email' },
        { key: 'role' },
        { key: 'actions' }
      ],
      items: [
        { name: 'John', email: 'john@abc.com', id: '1', role: 'Admin Editor Viewer' },
        { name: 'Jane', email: 'jane@abc.com', id: '2', role: 'Admin Editor Viewer' },
        { name: 'Jim', email: 'jim@abc.com', id: '3', role: 'Viewer' },
        { name: 'Sam', email: 'sam@abc.com', id:'4', role: 'Editor Viewer' },
        { name: 'Larry', email: 'larry@abc.com', id: '5', role: 'Viewer' },
        { name: 'Monica', email: 'monica@abc.com', id: '6', role: 'Editor Viewer' }
      ]
    }
  },
  methods: {
    increaseVal () {
      this.value++
    }
  },
  components: {
    BIconPencilSquare,
    BIconEye,
    BIconTrash
  }
}
</script>

<style>
.action-icon {
  margin-right: 1rem;
}
</style>