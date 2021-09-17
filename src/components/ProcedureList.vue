<template>
  <table class="tab-for-prod">
    <tr>
      <th>Step</th>
      <th>Status</th>
    </tr>
    <tr v-for="(data, i) in tableData" v-bind:key="i">
      <td>{{data.step}}</td>
      <td :class="data.status">{{data.status}}</td>
    </tr>
  </table>
</template>

<script>

export default ({
  name: 'List',
  data() {
    return {
      tableData: [
        {
          step: 'Step1',
          status: 'PASS',
        },
        {
          step: 'Step2',
          status: 'TIMEOUT',
        },
        {
          step: 'Step3',
          status: 'ERROR',
        },
        {
          step: 'Step4',
          status: 'PASS',
        },
      ],
    }
  },
});
</script>

<style>

</style>
