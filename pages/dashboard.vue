<script setup>
const realtime = {
  voltage: 220.8,
  current: 1.75,
  power: 385,
  pf: 0.92,
  frequency: 50,
  kwhTotal: 2.84,
  timestamp: '2026-01-05 01:00',
}

const dailyEnergy = [
  { date: '2025-01-01', kwh: 4.2, cost: 6500 },
  { date: '2025-01-02', kwh: 3.8, cost: 5900 },
]

const prediction = {
  kwh: 4.5,
  estimatedCost: 7000,
}
</script>

<template>
  <VRow>
    <!-- REALTIME STAT CARDS -->
    <VCol
      v-for="item in [
        { title: 'Voltage', value: realtime.voltage + ' V' },
        { title: 'Current', value: realtime.current + ' A' },
        { title: 'Power', value: realtime.power + ' W' },
        { title: 'Power Factor', value: realtime.pf },
        { title: 'Frequency', value: realtime.frequency + ' Hz' },
        { title: 'Total Energy', value: realtime.kwhTotal + ' kWh' },
      ]"
      :key="item.title"
      cols="12"
      md="2"
    >
      <VCard>
        <VCardText class="text-center">
          <div class="text-caption text-medium-emphasis">
            {{ item.title }}
          </div>
          <div class="text-h6 font-weight-bold mt-2">
            {{ item.value }}
          </div>
        </VCardText>
      </VCard>
    </VCol>

    <!-- REALTIME MONITORING -->
    <VCol
      cols="12"
      md="8"
    >
      <VCard>
        <VCardItem>
          <VCardTitle>Realtime Energy Monitoring</VCardTitle>
          <VCardSubtitle>
            Updated at {{ realtime.timestamp }}
          </VCardSubtitle>
        </VCardItem>

        <VCardText>
          <!-- Chart Placeholder -->
          <VSheet
            height="260"
            class="d-flex align-center justify-center"
            color="grey-lighten-4"
            rounded
          >
            <span class="text-medium-emphasis">
              Realtime chart placeholder
            </span>
          </VSheet>
        </VCardText>
      </VCard>
    </VCol>

    <!-- PREDICTION -->
    <VCol
      cols="12"
      md="4"
    >
      <VCard
        variant="tonal"
        color="primary"
      >
        <VCardItem>
          <VCardTitle>Tomorrow Prediction</VCardTitle>
          <VCardSubtitle>Estimated usage</VCardSubtitle>
        </VCardItem>

        <VCardText>
          <VList density="compact">
            <VListItem>
              <VListItemTitle>Energy</VListItemTitle>
              <template #append>
                <strong>{{ prediction.kwh }} kWh</strong>
              </template>
            </VListItem>

            <VListItem>
              <VListItemTitle>Estimated Cost</VListItemTitle>
              <template #append>
                <strong>Rp {{ prediction.estimatedCost.toLocaleString() }}</strong>
              </template>
            </VListItem>
          </VList>
        </VCardText>
      </VCard>
    </VCol>

    <!-- DAILY TABLE -->
    <VCol cols="12">
      <VCard>
        <VCardItem>
          <VCardTitle>Daily Energy Usage</VCardTitle>
          <VCardSubtitle>Consumption history</VCardSubtitle>
        </VCardItem>

        <VCardText>
          <VTable>
            <thead>
              <tr>
                <th>Date</th>
                <th>kWh</th>
                <th>Cost (Rp)</th>
              </tr>
            </thead>
            <tbody>
              <tr
                v-for="row in dailyEnergy"
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
