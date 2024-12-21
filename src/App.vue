<script setup>
import { ref, computed } from 'vue'
const bicycling = [
  { code: '01003', met: 14.0, description: 'Bicycling, mountain, uphill, vigorous' },
  { code: '01004', met: 16.0, description: 'Bicycling, mountain, competitive racing' },
  { code: '01008', met: 8.5, description: 'Bicycling, BMX' },
  { code: '01009', met: 8.5, description: 'Bicycling, mountain, general' },
  {
    code: '01010',
    met: 4.0,
    description: 'Bicycling, <10 mph, leisure, to work or for pleasure',
  },
  { code: '01011', met: 6.8, description: 'Bicycling, to/from work, self selected pace' },
  { code: '01013', met: 5.8, description: 'Bicycling, on dirt or farm road, moderate pace' },
  { code: '01014', met: 7.0, description: 'Bicycling, general' },
  { code: '01015', met: 4.3, description: 'Bicycling, self-selected easy pace' },
  { code: '01016', met: 7.0, description: 'Bicycling, self-selected moderate pace' },
  { code: '01017', met: 9.0, description: 'Bicycling, self-selected vigorous pace' },
  { code: '01018', met: 3.5, description: 'Bicycling, leisure 5.5 mph' },
  { code: '01019', met: 5.8, description: 'Bicycling, leisure, 9.4 mph' },
  {
    code: '01020',
    met: 6.8,
    description: 'Bicycling, 10-11.9 mph, leisure, slow, light effort',
  },
  {
    code: '01030',
    met: 8.0,
    description: 'Bicycling, 12-13.9 mph, leisure, moderate effort',
  },
  {
    code: '01040',
    met: 10.0,
    description: 'Bicycling, 14-15.9 mph, racing or leisure, fast, vigorous effort',
  },
  {
    code: '01050',
    met: 12.0,
    description:
      'Bicycling, 16-19 mph, racing/not drafting or >19 mph drafting, very fast, racing general',
  },
  { code: '01060', met: 16.8, description: 'Bicycling, >20 mph, racing, not drafting' },
  {
    code: '01065',
    met: 8.5,
    description: 'Bicycling, 12 mph, seated, hands on brake hoods or bar drops, 80 rpm',
  },
  {
    code: '01066',
    met: 9.0,
    description: 'Bicycling, 12 mph, standing, hands on brake hoods, 60 rpm',
  },
  { code: '01070', met: 5.0, description: 'Unicycling' },
  {
    code: '01080',
    met: 6.8,
    description: 'E-bike (electrically assisted) without electronic support',
  },
  {
    code: '01084',
    met: 6.0,
    description: 'E-bike (electrically assisted) with light electronic support',
  },
  {
    code: '01088',
    met: 4.0,
    description: 'E-bike (electrically assisted) with high electronic support',
  },
  { code: '01200', met: 6.8, description: 'Bicycling, stationary, general' },
  {
    code: '01210',
    met: 3.5,
    description: 'Bicycling, stationary, 25-30 watts, very light to light effort',
  },
  { code: '01214', met: 4.0, description: 'Bicycling, stationary, 50 watts, light effort' },
  {
    code: '01216',
    met: 5.0,
    description: 'Bicycling, stationary, 60 watts, light to moderate effort',
  },
  { code: '01218', met: 5.8, description: 'Bicycling, stationary, 70-80 watts' },
  {
    code: '01220',
    met: 6.0,
    description: 'Bicycling, stationary, 90-100 watts, moderate to vigorous',
  },
  { code: '01224', met: 6.8, description: 'Bicycling, stationary, 101-125 watts' },
  { code: '01228', met: 8.0, description: 'Bicycling, stationary, 126-150 watts' },
  { code: '01232', met: 10.3, description: 'Bicycling, stationary, 151-199 watts' },
  { code: '01236', met: 10.8, description: 'Bicycling, stationary, 200-229 watts, vigorous' },
  {
    code: '01240',
    met: 12.5,
    description: 'Bicycling, stationary, 230-250 watts, very vigorous',
  },
  {
    code: '01244',
    met: 13.8,
    description: 'Bicycling, stationary, 270-305 watts, very vigorous',
  },
  {
    code: '01248',
    met: 16.3,
    description: 'Bicycling, stationary, >325 watts, very vigorous',
  },
  { code: '01252', met: 5.5, description: 'Bicycling, concentric only, 100 W' },
  { code: '01254', met: 11.0, description: 'Bicycling, concentric only, 200 W' },
  { code: '01262', met: 2.3, description: 'Bicycling, eccentric only, 100 to 149 W' },
]
const gender = ref('male')
const weight = ref(97)
const age = ref(50)

function formatNumber(number) {
  return new Intl.NumberFormat('da-DK').format(number)
}

const bmr = computed(() => {
  const factor = gender.value === 'male' ? 24 : 22
  return weight.value * factor
})

const calBurn = (met) => {
  const number = formatNumber(bmr.value * (met / 24))
  return number
}
</script>

<template>
  <main>
    <div class="bg-gray-100 p-4 space-y-4 rounded-lg inline-flex justify-between gap-4 mb-6">
      <div class="flex gap-2 flex-col justify-between h-full rounded-lg">
        <div class="flex items-center gap-2">
          <span class="w-20">Alder:</span>
          <input type="number" v-model="age" class="px-4 py-2 bg-white rounded-lg" />
        </div>
        <div class="flex items-center gap-2">
          <span class="w-20">Køn:</span>
          <select v-model="gender" class="px-4 py-2 bg-white rounded-lg">
            <option value="male">Male</option>
            <option value="female">Female</option>
          </select>
        </div>
        <div class="flex items-center gap-2">
          <span class="w-20">Vægt:</span>
          <input type="number" v-model="weight" class="px-4 py-2 bg-white rounded-lg" />
        </div>
      </div>

      <div class="flex bg-white rounded-lg flex-col p-4 justify-center items-center">
        <div class="text-xs">Dit BRM</div>
        <div class="text-5xl font-bold">{{ bmr }}</div>
      </div>
    </div>

    <table class="w-full">
      <thead>
        <tr class="">
          <th class="text-left p-2">Kode</th>
          <th class="text-left p-2">Beskrivelse</th>
          <th class="text-right p-2">MET</th>
          <th class="text-right p-2">Kalorieforbrug pr. time</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="activity in bicycling" :key="activity.code" class="">
          <td class="px-2 py-1">{{ activity.code }}</td>
          <td class="px-2 py-1">{{ activity.description }}</td>
          <td class="px-2 py-1 text-right">{{ activity.met }}</td>
          <td class="text-right">{{ calBurn(activity.met) }}</td>
        </tr>
      </tbody>
    </table>
  </main>
</template>
