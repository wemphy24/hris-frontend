<template>
  <section class="py-[200px] flex flex-col items-center justify-center px-4">
    <div class="text-[32px] font-semibold text-dark mb-4">Select Companies</div>
    <div class="w-full card">
      <div class="form-group">
        <label class="text-grey">Companies</label>
        <p v-if="$fetchState.pending">Fetching companies...</p>
        <select
          v-else
          v-model="selectedCompany"
          name="companies"
          id=""
          class="appearance-none input-field form-icon-chevron_down"
        >
          <option
            v-for="company in companies.data.result.data"
            :value="company.id"
            :key="company.id"
          >
            {{ company.name }}
          </option>
        </select>
        <button
          type="button"
          @click="openCompany()"
          class="w-full btn btn-primary mt-[14px]"
        >
          Continue
        </button>
        <p class="text-center">or</p>
        <NuxtLink to="/companies/create" class="w-full btn btn-white border"
          >Create New Companies</NuxtLink
        >
      </div>
    </div>
  </section>
</template>

<script>
export default {
  middleware: 'auth',
  data() {
    return {
      companies: [],
      selectedCompany: '',
    }
  },
  async fetch() {
    this.companies = await this.$axios.get('/company')
  },
  methods: {
    openCompany() {
      this.$router.push({
        name: 'companies-id',
        params: {
          id: this.selectedCompany,
        },
      })
    },
  },
}
</script>
