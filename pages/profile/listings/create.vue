<script setup>
definePageMeta({
  layout: "custom"
})
const { makes } = useCars()

const info = useState('adInfo', () => {
  return {
    make: '',
    model: '',
    year: '',
    miles: '',
    price: '',
    city: '',
    seats: '',
    features: '',
    description: '',
    image: null
  }
})
const onChangeInput = (data, name) => {
  info.value[name] = data
}

const inputs = [
  {
    id: 1,
    title: 'Model *',
    name: 'model',
    placeholder: 'Civic',
  },
  {
    id: 2,
    title: 'Year *',
    name: 'year',
    placeholder: '2019',
  },
  {
    id: 3,
    title: 'Miles *',
    name: 'mile',
    placeholder: '10000',
  },
  {
    id: 4,
    title: 'City *',
    name: 'city',
    placeholder: 'Austin',
  },
  {
    id: 5,
    title: 'Number of Seats *',
    name: 'seats',
    placeholder: '5',
  },
  {
    id: 6,
    title: 'Features *',
    name: 'feature',
    placeholder: 'Leather Interior, No Accident',
  }
]

</script>
<template>
  <div>
    <div class="mt-24">
      <h1 class="text-6xl mt-24">Create a new listing</h1>
    </div>
    <div class="shadow rounded p-3 mt-5 flex flex-wrap justify-between">
      <CarAdSelect
        title="Make *"
        name="make"
        @changeInput="onChangeInput"
        :options="makes"
      />
      <CarAdInput
        v-for="input in inputs"
        :key="input.id"
        :title="input.title"
        :name="input.name"
        :placeholder="input.placeholder"
        @changeInput="onChangeInput"
      />
      <CarAdTextarea
        title="Description *"
        name="description"
        placeholder=""
        @changeInput="onChangeInput"
      />
      <CarAdImage @changeInput="onChangeInput" />
    </div>
  </div>
</template>