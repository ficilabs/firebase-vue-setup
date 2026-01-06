<script setup>
const history = [
  { date: '2025-01-01', kwh: 4.2, cost: 6500 },
  { date: '2025-01-02', kwh: 3.8, cost: 5900 },
  { date: '2025-01-03', kwh: 4.5, cost: 7000 },
]

const summary = {
  totalKwh: 12.5,
  totalCost: 19400,
  averageKwh: 4.16,
}
</script>

<template>
  <VRow>
    <!-- PAGE HEADER -->
    <VCol cols="12">
      <div class="d-flex align-center justify-space-between">
        <div>
          <h2 class="text-h5 font-weight-bold">Energy Usage History</h2>
          <p class="text-body-2 text-medium-emphasis">
            Daily electricity consumption
          </p>
        </div>
      </div>
    </VCol>

    <!-- SUMMARY CARDS -->
    <VCol cols="12" sm="4">
      <VCard>
        <VCardText class="text-center">
          <div class="text-caption text-medium-emphasis">
            Total Energy
          </div>
          <div class="text-h6 font-weight-bold mt-2">
            {{ summary.totalKwh }} kWh
          </div>
        </VCardText>
      </VCard>
    </VCol>

    <VCol cols="12" sm="4">
      <VCard>
        <VCardText class="text-center">
          <div class="text-caption text-medium-emphasis">
            Total Cost
          </div>
          <div class="text-h6 font-weight-bold mt-2">
            Rp {{ summary.totalCost.toLocaleString() }}
          </div>
        </VCardText>
      </VCard>
    </VCol>

    <VCol cols="12" sm="4">
      <VCard>
        <VCardText class="text-center">
          <div class="text-caption text-medium-emphasis">
            Average / Day
          </div>
          <div class="text-h6 font-weight-bold mt-2">
            {{ summary.averageKwh }} kWh
          </div>
        </VCardText>
      </VCard>
    </VCol>

    <!-- HISTORY TABLE -->
    <VCol cols="12">
      <VCard>
        <VCardItem>
          <VCardTitle>Daily History</VCardTitle>
          <VCardSubtitle>
            Electricity usage per day
          </VCardSubtitle>
        </VCardItem>

        <VCardText>
          <VTable>
            <thead>
              <tr>
                <th>Date</th>
                <th>Energy (kWh)</th>
                <th>Cost (Rp)</th>
              </tr>
            </thead>
            <tbody>
              <tr
                v-for="row in history"
                :key="row.date"
              >
                <td>{{ row.date }}</td>
                <td>{{ row.kwh }}</td>
                <td>{{ row.cost.toLocaleString() }}</td>
              </tr>
            </tbody>
          </VTable>
        </VCardText>
      </VCard>
    </VCol>
  </VRow>
</template>
