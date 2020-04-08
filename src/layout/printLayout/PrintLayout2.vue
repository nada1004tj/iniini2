<template>
  <div class="card shadow"
       :class="type === 'dark' ? 'bg-default': ''">
    <div class="card-header border-0"
         :class="type === 'dark' ? 'bg-transparent': ''">
      <div class="row align-items-center">
        <div class="col">
          <h3 class="mb-0" :class="type === 'dark' ? 'text-white': ''">
            {{title}}
          </h3>
        </div>
        <div class="col text-right">
          <base-button type="primary" size="sm">See all</base-button>
        </div>
      </div>
    </div>
    <div>
      <Print></Print>
    </div>
    <div class="card-footer d-flex justify-content-end"
         :class="type === 'dark' ? 'bg-transparent': ''">
        <PrintAAAA id="PrintAAAA"></PrintAAAA>
    </div>
  </div>
</template>
<script>
  import PrintAAAA from '@/layout/printLayout/PrintA4.vue'
  import Print from '@/components/Print.vue'

  export default {
    name: 'printLayout2',
    props: {
      type: {
        type: String
      },
      title: String
    },
    components: {
      PrintAAAA,
      Print
    }
  }
</script>
<style>
</style>
