<template>
<div class="flex flex-col dark:bg-gray-700 ml-24 w-11/12 shadow-lg sm:rounded-lg pl-2 pr-2 pt-2 pb-12 border-t border-gray-100">
  <h1 class="text-2xl text-gray-500 dark:text-white mb-4">Employees</h1>
  <div class="-my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
    <div class="py-2 align-middle inline-block min-w-full sm:px-6 lg:px-8">
      <div class="overflow-hidden border sm:rounded-lg border-gray-200">
        <table class="min-w-full divide-x divide-y divide-gray-200">
          <thead>
            <tr>
              <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 dark:text-white tracking-wider">
                Employee
              </th>
              <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 dark:text-white tracking-wider">
                Last login
              </th>
              <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 dark:text-white tracking-wider">
                Department
              </th>
              <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 dark:text-white tracking-wider">
                Status
              </th>
              <th scope="col" class="px-2 py-3 text-left text-xs font-medium text-gray-500 dark:text-white tracking-wider">
              </th>
            </tr>
          </thead>
          <tbody class="bg-white dark:bg-gray-700 divide-y divide-x divide-gray-200">
            <tr :key="user.id" v-for="user in users.slice(0, 5)">
              <td class="px-4 py-2 whitespace-nowrap">
                <div class="flex items-center">
                  <div class="flex-shrink-0 h-10 w-10">
                    <img class="h-10 w-10 rounded-full" :src="user.profile_img" :alt="user.first_name">
                  </div>
                  <div class="ml-4">
                    <div class="text-sm font-medium text-gray-900 dark:text-gray-300">
                      {{`${user.first_name} ${user.last_name}`}}
                    </div>
                    <div class="text-sm text-gray-500 dark:text-white">
                      {{user.email.toLowerCase()}}
                    </div>
                  </div>
                </div>
              </td>
              <td class="px-4 py-2 whitespace-nowrap">
                <div class="text-sm text-gray-900 dark:text-gray-300">{{formatDate(user.sessions)}}</div>
                <div class="text-sm text-gray-500 dark:text-white">{{getLastLogin(user.sessions)}}</div>
              </td>
              <td class="px-4 py-2 whitespace-nowrap text-sm text-gray-900 dark:text-gray-300">
                {{user.department}}
              </td>
              <td class="px-4 py-2 whitespace-nowrap">
                <span :class="`px-2 inline-flex text-xs leading-5 font-semibold rounded-full ${user.status ? 'text-green-500' : 'text-red-500'}`">
                  {{user.status ? 'Active' : 'Inactive'}}
                </span>
              </td>
              <td class="px-4 py-2 whitespace-nowrap text-sm text-gray-900 dark:text-gray-300">
                <button v-on:click="sayhi">⌄</button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import moment from 'moment'

export default {
    name: 'Table',
    props: {
    users: Array,
  },
    methods: {
      formatDate(date) {
        let latest = date.sort()[date.length - 1].slice(0, 10)
        let result = moment(latest, "YYYY-MM-DD").format("MMMM DD, YYYY")
        return result;
      },
      getLastLogin(date) {
        let latest = date.sort()[date.length - 1]
        let result = moment(latest).fromNow()
        return result;
      },
      sayhi() {
        alert(`Hi! I'm ready to start working at Videsk! :)`)
      }
    }
}
</script>
