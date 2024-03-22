<template>
  <section class="py-[200px] flex flex-col items-center justify-center px-4">
    <div class="text-[32px] font-semibold text-dark mb-4">Select Companies</div>
    <form class="w-full card">
      <div class="form-group">
        <label class="text-grey">Companies</label>
        <select
          name=""
          id=""
          class="appearance-none input-field form-icon-chevron_down"
        >
          <option value="" selected>Company Name</option>
        </select>
        <NuxtLink to="/" class="w-full btn btn-primary mt-[14px]">
          Continue
        </NuxtLink>
      </div>
    </form>
  </section>
</template>

<script>
export default {
  middleware: 'auth',
}
</script>

<style></style>
