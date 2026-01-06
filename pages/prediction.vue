<script setup>
const tomorrow = {
  kwh: 4.5,
  estimatedCost: 7000,
  confidence: 0.87,
}

const forecast = [
  { date: '2026-01-06', kwh: 4.5, cost: 7000 },
  { date: '2026-01-07', kwh: 4.3, cost: 6800 },
  { date: '2026-01-08', kwh: 4.7, cost: 7200 },
]
</script>

<template>
  <VRow>
    <!-- PAGE HEADER -->
    <VCol cols="12">
      <div class="d-flex align-center justify-space-between">
        <div>
          <h2 class="text-h5 font-weight-bold">Energy Prediction</h2>
          <p class="text-body-2 text-medium-emphasis">
            Estimated electricity usage
          </p>
        </div>

        <VChip color="info" variant="tonal">
          AI Forecast
        </VChip>
      </div>
    </VCol>

    <!-- TOMORROW PREDICTION -->
    <VCol cols="12" md="4">
      <VCard variant="tonal" color="primary">
        <VCardItem>
          <VCardTitle>Tomorrow</VCardTitle>
          <VCardSubtitle>
            Predicted usage
          </VCardSubtitle>
        </VCardItem>

        <VCardText>
          <div class="text-center mb-4">
            <div class="text-caption text-medium-emphasis">
              Energy Consumption
            </div>
            <div class="text-h5 font-weight-bold">
              {{ tomorrow.kwh }} kWh
            </div>
          </div>

          <VDivider class="my-3" />

          <div class="d-flex justify-space-between">
            <span class="text-body-2">Estimated Cost</span>
            <strong>
              Rp {{ tomorrow.estimatedCost.toLocaleString() }}
            </strong>
          </div>

          <div class="d-flex justify-space-between mt-2">
            <span class="text-body-2">Prediction Confidence</span>
            <strong>
              {{ Math.round(tomorrow.confidence * 100) }}%
            </strong>
          </div>
        </VCardText>
      </VCard>
    </VCol>

    <!-- FORECAST DETAILS -->
    <VCol cols="12" md="8">
      <VCard>
        <VCardItem>
          <VCardTitle>Upcoming Forecast</VCardTitle>
          <VCardSubtitle>
            Next days estimation
          </VCardSubtitle>
        </VCardItem>

        <VCardText>
          <VTable>
            <thead>
              <tr>
                <th>Date</th>
                <th>Energy (kWh)</th>
                <th>Estimated Cost (Rp)</th>
              </tr>
            </thead>
            <tbody>
              <tr
                v-for="row in forecast"
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

    <!-- PREDICTION NOTE -->
    <VCol cols="12">
      <VAlert
        type="info"
        variant="tonal"
        border="start"
      >
        Prediction is based on historical usage patterns and may change due to
        weather, appliance usage, or operational behavior.
      </VAlert>
    </VCol>
  </VRow>
</template>
