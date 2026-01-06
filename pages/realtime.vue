<script setup>
const realtime = {
  voltage: 220.8,
  current: 1.75,
  power: 385,
  pf: 0.92,
  frequency: 50,
  kwhtotal: 2.84,
  timestamp: '2026-01-05 12:10:30',
}
</script>

<template>
  <VRow>
    <VCol cols="12">
      <div class="d-flex align-center justify-space-between">
        <div>
          <h2 class="text-h5 font-weight-bold">
            Realtime Energy Monitoring
          </h2>
          <p class="text-body-2 text-medium-emphasis">
            Live electrical measurement
          </p>
        </div>

        <VChip
          color="success"
          variant="tonal"
        >
          ● LIVE
        </VChip>
      </div>
    </VCol>

    <VCol
      v-for="item in [
        { label: 'Voltage', value: realtime.voltage, unit: 'V' },
        { label: 'Current', value: realtime.current, unit: 'A' },
        { label: 'Power', value: realtime.power, unit: 'W' },
        { label: 'Power Factor', value: realtime.pf, unit: '' },
        { label: 'Frequency', value: realtime.frequency, unit: 'Hz' },
        { label: 'Total Energy', value: realtime.kwhtotal, unit: 'kWh' },
      ]"
      :key="item.label"
      cols="12"
      sm="6"
      md="4"
      lg="2"
    >
      <VCard>
        <VCardText class="text-center">
          <div class="text-caption text-medium-emphasis">
            {{ item.label }}
          </div>
          <div class="text-h6 font-weight-bold mt-2">
            {{ item.value }} {{ item.unit }}
          </div>
        </VCardText>
      </VCard>
    </VCol>

    <VCol
      cols="12"
      md="8"
    >
      <VCard>
        <VCardItem>
          <VCardTitle>Realtime Details</VCardTitle>
          <VCardSubtitle>
            Last updated: {{ realtime.timestamp }}
          </VCardSubtitle>
        </VCardItem>

        <VCardText>
          <VTable density="comfortable">
            <tbody>
              <tr>
                <td>Voltage</td>
                <td>{{ realtime.voltage }} V</td>
              </tr>
              <tr>
                <td>Current</td>
                <td>{{ realtime.current }} A</td>
              </tr>
              <tr>
                <td>Power</td>
                <td>{{ realtime.power }} W</td>
              </tr>
              <tr>
                <td>Power Factor</td>
                <td>{{ realtime.pf }}</td>
              </tr>
              <tr>
                <td>Frequency</td>
                <td>{{ realtime.frequency }} Hz</td>
              </tr>
              <tr>
                <td>Total Energy</td>
                <td>{{ realtime.kwhtotal }} kWh</td>
              </tr>
            </tbody>
          </VTable>
        </VCardText>
      </VCard>
    </VCol>

    <VCol
      cols="12"
      md="4"
    >
      <VCard>
        <VCardItem>
          <VCardTitle>Realtime Visualization</VCardTitle>
          <VCardSubtitle>
            Power / Voltage graph
          </VCardSubtitle>
        </VCardItem>

        <VCardText>
          <VSheet
            height="220"
            rounded
            class="d-flex align-center justify-center"
            color="grey-lighten-4"
          >
            <span class="text-medium-emphasis">
              Chart placeholder (client-only later)
            </span>
          </VSheet>
        </VCardText>
      </VCard>
    </VCol>
  </VRow>
</template>
