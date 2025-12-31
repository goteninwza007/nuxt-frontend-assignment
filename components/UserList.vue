<template>
  <div>
    <button @click="toggleSort" class="sort-btn">
      Sort by Age: {{ isAsc ? 'Min - Max' : 'Max - Min' }}
    </button>

    <table class="table">
      <thead>
        <tr>
          <th>Name</th>
          <th>Email</th>
          <th>Age</th>
          <th>Role</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="user in sortedUsers" :key="user.id">
          <td>{{ user.name }}</td>
          <td>{{ user.email }}</td>
          <td>{{ user.age }}</td>
          <td>{{ user.role }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script lang="ts">
import type { User } from '~/pages/users.vue';

export default {
  props: {
    users: {
      type: Array as () => User[],
      required: true
    }
  },
  data() {
    return {
      isAsc: true
    }
  },

  computed: {
    sortedUsers() {
      return [...this.users].sort((a, b) => {
        return this.isAsc ? a.age - b.age : b.age - a.age
      })
    }
  },

  methods: {
    toggleSort() {
      this.isAsc = !this.isAsc
    }
  }
}
</script>

<style scoped>
.sort-btn {
  margin-bottom: 12px;
  padding: 6px 12px;
  cursor: pointer;
}

.table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  padding: 8px;
  border: 1px solid #ddd;
}

th {
  background: #f3f4f6;
}
</style>
