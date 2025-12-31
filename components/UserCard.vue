<template>
  <div class="user-card">
    <div class="header">
      <h3>{{ fullName }}</h3>
      <span :class="['status', user.isActive ? 'active' : 'inactive']">
        {{ user.isActive ? 'Active' : 'Inactive' }}
      </span>
    </div>

    <p><strong>Email:</strong> {{ user.email }}</p>
    <p><strong>Phone:</strong> {{ user.phone }}</p>
    <p><strong>Age:</strong> {{ user.age }}</p>
    <p><strong>City:</strong> {{ user.city }}</p>

    <div class="tags">
      <span
        v-for="tag in user.tags"
        :key="tag"
        class="tag"
      >
        {{ tag }}
      </span>
    </div>

    <small class="date">
      Created at: {{ formattedDate }}
    </small>
  </div>
</template>

<script lang="ts">
import type { User } from '~/data/mockUsers'

export default {
  props: {
    user: {
      type: Object as () => User,
      required: true
    }
  },

  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`
    },

    formattedDate() {
      return new Date(this.user.createdAt).toLocaleDateString()
    }
  }
}
</script>

<style scoped lang="scss">
.user-card {
  padding: 16px;
  border-radius: 10px;
  background: #f5f5f5;
  display: flex;
  flex-direction: column;
  gap: 6px;
  word-break: break-word;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.status {
  padding: 2px 8px;
  border-radius: 12px;
  font-size: 12px;

  &.active {
    background: #d1fae5;
    color: #065f46;
  }

  &.inactive {
    background: #fee2e2;
    color: #991b1b;
  }
}

.tags {
  display: flex;
  gap: 6px;
  flex-wrap: wrap;
  margin-top: 6px;
}

.tag {
  background: #e5e7eb;
  padding: 2px 8px;
  border-radius: 8px;
  font-size: 12px;
}

.date {
  margin-top: 8px;
  font-size: 12px;
  color: #6b7280;
}
</style>
