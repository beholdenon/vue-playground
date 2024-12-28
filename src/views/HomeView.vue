<script setup>
import { ref, reactive, computed } from 'vue'

const sortBy = ref('state')
const sortDir = ref('asc')
const filteredState = ref('')

const stores = reactive([
  {
    store: 'Century City',
    phone: '310-772-2100',
    address: '10250 Santa Monica Blvd',
    city: 'Los Angeles',
    state: 'CA',
    zip: '90067',
    mattresses: '1',
    furniture: '',
    rugs: '1',
  },
  {
    store: 'Fashion Valley',
    phone: '619-610-6400',
    address: '7057 Friars Road',
    city: 'San Diego',
    state: 'CA',
    zip: '92108',
    mattresses: '1',
    furniture: '',
    rugs: '',
  },
  {
    store: 'Newport Fashion Island',
    phone: '949-792-6600',
    address: '701 Newport Center DR',
    city: 'Newport Beach',
    state: 'CA',
    zip: '92660',
    mattresses: '1',
    furniture: '',
    rugs: '',
  },
  {
    store: 'San Francisco Centre',
    phone: '415-856-5300',
    address: '845 Market Street',
    city: 'San Francisco',
    state: 'CA',
    zip: '94103',
    mattresses: '1',
    furniture: '',
    rugs: '',
  },
  {
    store: 'Sherman Oaks Fashion Square',
    phone: '818-325-2200',
    address: '14060 Riverside Drive',
    city: 'Sherman Oaks',
    state: 'CA',
    zip: '91423',
    mattresses: '1',
    furniture: '',
    rugs: '',
  },
  {
    store: 'South Coast Plaza',
    phone: '714-824-4600',
    address: '3333 South Bristol Street',
    city: 'Costa Mesa',
    state: 'CA',
    zip: '92626',
    mattresses: '1',
    furniture: '',
    rugs: '',
  },
  {
    store: 'Stanford',
    phone: '650-463-2000',
    address: '1 Stanford Shopping Center',
    city: 'Palo Alto',
    state: 'CA',
    zip: '94304',
    mattresses: '1',
    furniture: '',
    rugs: '',
  },
  {
    store: 'Valley Fair',
    phone: '408-878-6200',
    address: '2847 Stevens Creek Boulevard',
    city: 'San Jose',
    state: 'CA',
    zip: '95128',
    mattresses: '1',
    furniture: '',
    rugs: '',
  },
  {
    store: 'Norwalk',
    phone: '203-295-6000',
    address: '100 North Water Street',
    city: 'Norwalk',
    state: 'CT',
    zip: '06854',
    mattresses: '1',
    furniture: '1',
    rugs: '1',
  },
  {
    store: 'Aventura',
    phone: '305-792-1000',
    address: '19555 Biscayne Blvd.',
    city: 'Aventura',
    state: 'FL',
    zip: '33180',
    mattresses: '1',
    furniture: '1',
    rugs: '1',
  },
  {
    store: 'Boca Raton Town Center',
    phone: '561-394-2000',
    address: '5840 Glades Road',
    city: 'Boca Raton',
    state: 'FL',
    zip: '33431',
    mattresses: '1',
    furniture: '1',
    rugs: '1',
  },
  {
    store: 'Orlando, The Mall at Millenia',
    phone: '407-264-2400',
    address: '4152 Conroy Rd.',
    city: 'Orlando',
    state: 'FL',
    zip: '32839',
    mattresses: '1',
    furniture: '1',
    rugs: '1',
  },
  {
    store: 'Palm Beach Gardens',
    phone: '561-625-2000',
    address: '3105 PGA Blvd. ',
    city: 'Palm Beach Gardens',
    state: 'FL',
    zip: '33410',
    mattresses: '1',
    furniture: '1',
    rugs: '1',
  },
  {
    store: 'Lenox Square',
    phone: '404-495-2800',
    address: '3393 Peachtree Rd',
    city: 'NE Atlanta',
    state: 'GA',
    zip: '30326',
    mattresses: '1',
    furniture: '',
    rugs: '',
  },
  {
    store: 'North Michigan Avenue',
    phone: '312-440-4460',
    address: '900 North Michigan Avenue',
    city: 'Chicago',
    state: 'IL',
    zip: '60611',
    mattresses: '1',
    furniture: '1',
    rugs: '1',
  },
  {
    store: 'Old Orchard',
    phone: '847-675-5200',
    address: '4963 Old Orchard Center',
    city: 'Skokie',
    state: 'IL',
    zip: '60077',
    mattresses: '1',
    furniture: '',
    rugs: '',
  },
  {
    store: 'Chesnut Hill',
    phone: '617-630-6000',
    address: '225 Boylston St.',
    city: 'Newton',
    state: 'MA',
    zip: '02467',
    mattresses: '1',
    furniture: '1',
    rugs: '1',
  },
  {
    store: 'Chevy Chase',
    phone: '240-744-3700',
    address: '5300 Western Avenue',
    city: 'Chevy Chase',
    state: 'MD',
    zip: '20815',
    mattresses: '1',
    furniture: '1',
    rugs: '',
  },
  {
    store: 'Bergen Shops at Riverdale',
    phone: '201-457-2000',
    address: '400 Hackensack Ave.',
    city: 'Hackensack',
    state: 'NJ',
    zip: '07602',
    mattresses: '1',
    furniture: '1',
    rugs: '1',
  },
  {
    store: 'Short Hills',
    phone: '973-548-2200',
    address: '1200 Morris Tpke',
    city: 'Short Hills',
    state: 'NJ',
    zip: '07078',
    mattresses: '1',
    furniture: '',
    rugs: '1',
  },
  {
    store: 'Willowbrook',
    phone: '973-582-2400',
    address: '1400 Willowbrook Mall',
    city: 'Wayne',
    state: 'NJ',
    zip: '07470',
    mattresses: '1',
    furniture: '1',
    rugs: '',
  },
  {
    store: '59th Street',
    phone: '212-705-2000',
    address: '1000 Third Ave',
    city: 'New York',
    state: 'NY',
    zip: '10022',
    mattresses: '1',
    furniture: '1',
    rugs: '1',
  },
  {
    store: 'Huntington',
    phone: '631-425-6700',
    address: '270 Walt Whitman Road',
    city: 'Huntington Station',
    state: 'NY',
    zip: '11746',
    mattresses: '1',
    furniture: '',
    rugs: '',
  },
  {
    store: 'Roosevelt Field Mall',
    phone: '516-873-2700',
    address: '630 Old Country Rd',
    city: 'Garden City',
    state: 'NY',
    zip: '11530',
    mattresses: '1',
    furniture: '1',
    rugs: '1',
  },
  {
    store: 'White Plains',
    phone: '914-684-6300',
    address: '175 Bloomingdale Road',
    city: 'White Plains',
    state: 'NY',
    zip: '10605',
    mattresses: '1',
    furniture: '1',
    rugs: '1',
  },
  {
    store: 'King of Prussia',
    phone: '610-337-6300',
    address: '660 West Dekalb Pike',
    city: 'King of Prussia',
    state: 'PA',
    zip: '19406',
    mattresses: '1',
    furniture: '1',
    rugs: '1',
  },
  {
    store: 'Willow Grove',
    phone: '215-706-3300',
    address: '2400 West Moreland Park Rd',
    city: 'Willow Grove',
    state: 'PA',
    zip: '19090',
    mattresses: '1',
    furniture: '1',
    rugs: '1',
  },
  {
    store: "Tyson's Corner",
    phone: '703-556-4600',
    address: '8100 Tyson Corner Center',
    city: 'McLean',
    state: 'VA',
    zip: '22102',
    mattresses: '1',
    furniture: '1',
    rugs: '1',
  },
])

const stateLabelValues = [
  { label: 'Alabama', value: 'AL' },
  { label: 'Alaska', value: 'AK' },
  { label: 'American Samoa', value: 'AS' },
  { label: 'Arizona', value: 'AZ' },
  { label: 'Arkansas', value: 'AR' },
  { label: 'California', value: 'CA' },
  { label: 'Colorado', value: 'CO' },
  { label: 'Connecticut', value: 'CT' },
  { label: 'Delaware', value: 'DE' },
  { label: 'District of Columbia', value: 'DC' },
  { label: 'States of Micronesia', value: 'FM' },
  { label: 'Florida', value: 'FL' },
  { label: 'Georgia', value: 'GA' },
  { label: 'Guam', value: 'GU' },
  { label: 'Hawaii', value: 'HI' },
  { label: 'Idaho', value: 'ID' },
  { label: 'Illinois', value: 'IL' },
  { label: 'Indiana', value: 'IN' },
  { label: 'Iowa', value: 'IA' },
  { label: 'Kansas', value: 'KS' },
  { label: 'Kentucky', value: 'KY' },
  { label: 'Louisiana', value: 'LA' },
  { label: 'Maine', value: 'ME' },
  { label: 'Marshall Islands', value: 'MH' },
  { label: 'Maryland', value: 'MD' },
  { label: 'Massachusetts', value: 'MA' },
  { label: 'Michigan', value: 'MI' },
  { label: 'Minnesota', value: 'MN' },
  { label: 'Mississippi', value: 'MS' },
  { label: 'Missouri', value: 'MO' },
  { label: 'Montana', value: 'MT' },
  { label: 'Nebraska', value: 'NE' },
  { label: 'Nevada', value: 'NV' },
  { label: 'New Hampshire', value: 'NH' },
  { label: 'New Jersey', value: 'NJ' },
  { label: 'New Mexico', value: 'NM' },
  { label: 'New York', value: 'NY' },
  { label: 'North Carolina', value: 'NC' },
  { label: 'North Dakota', value: 'ND' },
  { label: 'Northern Mariana Islands', value: 'MP' },
  { label: 'Ohio', value: 'OH' },
  { label: 'Oklahoma', value: 'OK' },
  { label: 'Oregan', value: 'OR' },
  { label: 'Palau', value: 'PW' },
  { label: 'Pennsilvania', value: 'PA' },
  { label: 'Puerto Rico', value: 'PR' },
  { label: 'Rhode Island', value: 'RI' },
  { label: 'South Carolina', value: 'SC' },
  { label: 'South Dakota', value: 'SD' },
  { label: 'Tennessee', value: 'TN' },
  { label: 'Texas', value: 'TX' },
  { label: 'Utah', value: 'UT' },
  { label: 'Vermont', value: 'VT' },
  { label: 'Virgin Islands', value: 'VI' },
  { label: 'Virginia', value: 'VA' },
  { label: 'Washington', value: 'WA' },
  { label: 'West Virginia', value: 'WV' },
  { label: 'Wisconsin', value: 'WI' },
  { label: 'Wyoming', value: 'WY' },
]

const headers = [
  { name: 'state', sort: true },
  { name: 'store', sort: true },
  { name: 'address' },
  { name: 'mattresses', sort: true, classes: 'text-center' },
  { name: 'furniture', sort: true, classes: 'text-center' },
  { name: 'rugs', sort: true, classes: 'text-center' },
]

const sortedStores = computed(() => {
  let newStores = [...stores]
  let modifier = 1
  if (sortDir.value === 'desc') modifier = -1
  if (filteredState.value) {
    newStores = [...newStores].filter((store) => store.state === filteredState.value)
  }
  return [...newStores].sort((a, b) => {
    if (a[sortBy.value] < b[sortBy.value]) return -1 * modifier
    if (a[sortBy.value] > b[sortBy.value]) return 1 * modifier
    return 0
  })
})

const uniqueStates = computed(() => {
  let states = []
  stores.forEach((store) => states.push(store.state))
  let s = new Set(states)
  return [...s]
})

const setSort = (col, sort) => {
  if (!sort) return
  if (sortBy.value === col) {
    sortDir.value === 'asc' ? (sortDir.value = 'desc') : (sortDir.value = 'asc')
  } else {
    sortDir.value = 'asc'
    sortBy.value = col
  }
}

const getState = (abr) => {
  let name = ''
  stateLabelValues.forEach((s) => {
    if (s.value === abr) {
      name = s.label
    }
  })
  return name
}
</script>

<template>
  <div class="grid-container">
    <div class="grid-x module no-padding-bottom headline-large text-left">
      <div class="cell small-11">
        <h1>Furniture, Mattresses & Rugs Locations</h1>
        <p>
          Furniture, Mattresses and Rugs can be found at the following Bloomingdale's Store
          Locations. Please call or visit for more information.
        </p>
      </div>
    </div>
  </div>
  <div class="grid-container">
    <div class="grid-x module no-padding-bottom half-padding-top headline-large text-left">
      <div class="cell small-11">
        <div class="filter">
          <span class="filterText">Filter by State:</span>
          <select v-model="filteredState">
            <option value="">View All</option>
            <option v-for="state in uniqueStates" :value="state">
              {{ getState(state) }}
            </option>
          </select>
        </div>
      </div>
    </div>
  </div>

  <div class="grid-container mobileStoresOuter">
    <div class="grid-x module half-padding-top text-left">
      <div class="cell small-11">
        <ul class="mobileStores">
          <li v-for="store in sortedStores">
            <h2 class="mobileStoreName">{{ store.store }}</h2>
            <p>{{ store.address }}, {{ store.city }}, {{ store.state }} {{ store.zip }}</p>
            <p><strong>Phone:</strong> {{ store.phone }}</p>

            <ul class="mobileServices">
              <li>
                <div class="mobileHeader">Mattresses</div>
                <div v-if="store.mattresses === '1'" class="checkMark"></div>
                <div v-else class="xMark"></div>
              </li>
              <li>
                <div class="mobileHeader">Furniture</div>
                <div v-if="store.furniture === '1'" class="checkMark"></div>
                <div v-else class="xMark"></div>
              </li>
              <li>
                <div class="mobileHeader">Rugs</div>
                <div v-if="store.rugs === '1'" class="checkMark"></div>
                <div v-else class="xMark"></div>
              </li>
            </ul>
          </li>
        </ul>
      </div>
    </div>
  </div>

  <div class="grid-container desktopStoresOuter">
    <div class="grid-x module half-padding-top text-left">
      <div class="cell small-11">
        <table class="desktopStores">
          <thead>
            <tr>
              <th
                v-for="header in headers"
                :class="header.classes"
                @click="setSort(header.name, header.sort)"
              >
                {{ header.name }}
                <span v-if="sortBy === header.name">{{
                  sortDir === 'asc' ? '&darr;' : '&uarr;'
                }}</span>
                <span v-else class="no-opacity">&darr;</span>
              </th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="store in sortedStores">
              <td>
                <strong>{{ store.state }}</strong>
              </td>
              <td>{{ store.store }}</td>
              <td>
                {{ store.address }}<br />{{ store.city }}, {{ store.state }} {{ store.zip }}<br />{{
                  store.phone
                }}
              </td>
              <td class="text-center">
                <div v-if="store.mattresses === '1'" class="checkMark"></div>
                <div v-else class="xMark"></div>
              </td>
              <td class="text-center">
                <div v-if="store.furniture === '1'" class="checkMark"></div>
                <div v-else class="xMark"></div>
              </td>
              <td class="text-center">
                <div v-if="store.rugs === '1'" class="checkMark"></div>
                <div v-else class="xMark"></div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>
