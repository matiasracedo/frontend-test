<template>
  <div class="app-container bg-gray-50 dark:bg-gray-700" :class="(mode === 'dark') ? 'dark' : 'light'">
    <Header :mode="mode" @toggle="toggle" />
    <div class="container flex">
      <div class="flex-auto">
        <PieChartContainer v-if="reports.length > 0" :reports="reports" />
      </div>
      <div class="flex-auto">
        <Table :users="users" />
      </div>
    </div>
  </div>
</template>

<script>
import PieChartContainer from './components/ChartContainer'
import Table from './components/Table'
import Header from './components/Header'

export default {
  name: 'app',
  components: {
    Header,
    PieChartContainer,
    Table
  },
  data() {
    return {
      mode: 'dark',
      reports: [],
      users: []
    }
  },
  methods: {
    toggle() {
      if (this.mode === 'dark') {
        this.mode = 'light'
      } else {
        this.mode = 'dark'
      }
    }
  },
  async created() {
    // Reports
    const reportResponse = await fetch('/api/reports');
    const result = await reportResponse.json();
    this.reports = this.reports.concat(result.reports);
    // Users
    const userResponse = await fetch('/api/users');
    const usersResult = await userResponse.json();
    this.users = this.users.concat(usersResult.users);
  }
}
</script>

