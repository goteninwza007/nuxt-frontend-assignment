<template>
    <div class="page">
        <div class="grid">
            <UserCard v-for="user in filteredDuplicateUsers" :key="user.firstName + user.lastName" :user="user" />
        </div>
    </div>
</template>

<script lang="ts">
import { mockUsers, type User } from '~/data/mockUsers';

export default {
    setup() {
        return { mockUsers }
    },
    methods: {
        normalizePhone(phone: string): string {
            const digits = phone.replace(/\D/g, '')

            if (digits.startsWith('66')) {
                return '0' + digits.slice(2)
            }

            return digits
        },

        isSameUser(a: User, b: User): boolean {
            const isSameEmail =
                a.email.toLowerCase() === b.email.toLowerCase()

            const isSameNameAndPhone =
                `${a.firstName} ${a.lastName}`.toLowerCase() ===
                `${b.firstName} ${b.lastName}`.toLowerCase() &&
                this.normalizePhone(a.phone) === this.normalizePhone(b.phone)

            return isSameEmail || isSameNameAndPhone
        }
    },
    computed: {
        filteredDuplicateUsers() {
            const result: User[] = []

            for (const user of mockUsers) {
                const isDuplicate = result.some(existingUser =>
                    this.isSameUser(existingUser, user)
                )

                if (!isDuplicate) {
                    result.push(user)
                }
            }

            return result
        }
    }
}
</script>

<style scoped lang="scss">
.page {
    padding: 24px;
}

select {
    margin-bottom: 16px;
    padding: 8px;
}

.grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
    gap: 16px;
}
</style>
