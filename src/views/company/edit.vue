<template>
  <div class="app-container">
    <company-form :is-edit="true" />
  </div>
</template>

<script>
import CompanyForm from './components/CompanyForm'

export default {
  name: 'EditCompany',
  components: { CompanyForm }
}
</script>