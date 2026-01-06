<script setup>
const realtime = {
  voltage: 220.8,
  current: 1.75,
  power: 385,
  kwhToday: 4.1,
}

const device = {
  name: 'Main Energy Meter',
  status: 'online',
  lastSeen: '2026-01-05 12:20',
}

const prediction = {
  tomorrowKwh: 4.5,
  estimatedCost: 7000,
}
</script>

<template>
  <VRow>
    <!-- PAGE HEADER -->
    <VCol cols="12">
      <div class="d-flex align-center justify-space-between">
        <div>
          <h2 class="text-h5 font-weight-bold">
            Dashboard
          </h2>
          <p class="text-body-2 text-medium-emphasis">
            Energy monitoring overview
          </p>
        </div>

        <VChip
          color="success"
          variant="tonal"
        >
          System Online
        </VChip>
      </div>
    </VCol>

    <!-- REALTIME KPI -->
    <VCol
      cols="12"
      sm="6"
      md="3"
    >
      <VCard>
        <VCardText class="text-center">
          <div class="text-caption text-medium-emphasis">
            Voltage
          </div>
          <div class="text-h6 font-weight-bold mt-2">
            {{ realtime.voltage }} V
          </div>
        </VCardText>
      </VCard>
    </VCol>

    <VCol
      cols="12"
      sm="6"
      md="3"
    >
      <VCard>
        <VCardText class="text-center">
          <div class="text-caption text-medium-emphasis">
            Current
          </div>
          <div class="text-h6 font-weight-bold mt-2">
            {{ realtime.current }} A
          </div>
        </VCardText>
      </VCard>
    </VCol>

    <VCol
      cols="12"
      sm="6"
      md="3"
    >
      <VCard>
        <VCardText class="text-center">
          <div class="text-caption text-medium-emphasis">
            Power
          </div>
          <div class="text-h6 font-weight-bold mt-2">
            {{ realtime.power }} W
          </div>
        </VCardText>
      </VCard>
    </VCol>

    <VCol
      cols="12"
      sm="6"
      md="3"
    >
      <VCard
        variant="tonal"
        color="primary"
      >
        <VCardText class="text-center">
          <div class="text-caption">
            Energy Today
          </div>
          <div class="text-h6 font-weight-bold mt-2">
            {{ realtime.kwhToday }} kWh
          </div>
        </VCardText>
      </VCard>
    </VCol>

    <!-- DEVICE STATUS -->
    <VCol
      cols="12"
      md="4"
    >
      <VCard>
        <VCardItem>
          <VCardTitle>Device Status</VCardTitle>
          <VCardSubtitle>Main meter</VCardSubtitle>
        </VCardItem>

        <VCardText>
          <div class="d-flex justify-space-between">
            <span>Status</span>
            <VChip
              :color="device.status === 'online' ? 'success' : 'error'"
              size="small"
            >
              {{ device.status }}
            </VChip>
          </div>

          <div class="d-flex justify-space-between mt-2">
            <span>Last Seen</span>
            <span>{{ device.lastSeen }}</span>
          </div>
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
        color="info"
      >
        <VCardItem>
          <VCardTitle>Tomorrow Prediction</VCardTitle>
        </VCardItem>

        <VCardText>
          <div class="text-center">
            <div class="text-h6 font-weight-bold">
              {{ prediction.tomorrowKwh }} kWh
            </div>
            <div class="text-caption mt-1">
              Estimated Cost: Rp {{ prediction.estimatedCost.toLocaleString() }}
            </div>
          </div>
        </VCardText>
      </VCard>
    </VCol>

    <!-- QUICK ACCESS -->
    <VCol
      cols="12"
      md="4"
    >
      <VCard>
        <VCardItem>
          <VCardTitle>Quick Access</VCardTitle>
          <VCardSubtitle>Navigation</VCardSubtitle>
        </VCardItem>

        <VCardText>
          <VList density="compact">
            <VListItem
              to="/energy/realtime"
              link
            >
              <VListItemTitle>Realtime Monitoring</VListItemTitle>
            </VListItem>
            <VListItem
              to="/energy/history"
              link
            >
              <VListItemTitle>Usage History</VListItemTitle>
            </VListItem>
            <VListItem
              to="/energy/prediction"
              link
            >
              <VListItemTitle>Prediction</VListItemTitle>
            </VListItem>
            <VListItem
              to="/device"
              link
            >
              <VListItemTitle>Device</VListItemTitle>
            </VListItem>
            <VListItem
              to="/settings"
              link
            >
              <VListItemTitle>Settings</VListItemTitle>
            </VListItem>
          </VList>
        </VCardText>
      </VCard>
    </VCol>
  </VRow>
</template>
