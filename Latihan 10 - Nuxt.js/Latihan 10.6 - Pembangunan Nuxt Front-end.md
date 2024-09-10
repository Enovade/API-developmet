[[_TOC_]]

# Latihan 10.6: Pembangunan Nuxt Front-end

Latihan ini adalah untuk menunjukkan pemahaman pembangunan **Nuxt Front-end** yang akan menggunakan **Nuxt Pages, Layouts, Components** yang diwujudkan dari latihan sebelum ini.

Latihan ini adalah sambungan dari latihan [Latihan 5: Nuxt Components](https://code.cloud-connect.asia/msp/akademi-cloud-connect/training-modules/pembangunan-aplikasi-moden/-/blob/master/Latihan%2011/Latihan%205%20-%20Nuxt%20Components.md)


# Langkah 1.0: Laman Login

## Langkah 1.1: Ubah Laman Login

* Di VS Code, buka fail **login.vue** di direktori **pages**, padam kod sedia ada, salin dan tampal kod berikut

```vue
<template>
  <BContainer fluid>
    <BRow align-h="center">
      <BCol alignSelf="center" lg=5>
        <h1 style="text-align: center;">Laman Login</h1>
        <BForm @submit="onSubmit" @reset="onReset" v-if="show">
          <BFormGroup
            id="input-group-1"
            label="Emel:"
            label-for="input-1"
            description="Emel yang sah."
          >
            <BFormInput
              id="input-1"
              v-model="form.emel"
              type="email"
              placeholder="Masukkan emel"
              required
            />
          </BFormGroup>

          <BFormGroup 
            id="input-group-2"
            label="Katalaluan:"
            label-for="input-2"
            description="Katalaluan yang sah."
          >
            <BFormInput
              id="input-2"
              v-model="form.katalaluan"
              type="password"
              placeholder="Masukkan katalaluan"
              required />
          </BFormGroup>

          <BButton type="submit" variant="primary">Hantar</BButton>
          <BButton type="reset" variant="danger">Reset</BButton>
        </BForm>

        <BCard class="mt-3" header="Form Data Result">
          <pre class="m-0">{{ form }}</pre>
        </BCard>

        <div style="text-align: center;">
          <NuxtLink to="/"><Icon name="mdi:home-circle-outline" size="2em" />&nbsp;Utama</NuxtLink>
        </div>
      </BCol>
    </BRow>
  </BContainer>
</template>

<script setup lang="ts">
definePageMeta({
  layout: false,
});

const form = reactive({
  emel: '',
  katalaluan: ''
})
const show = ref(true)

const onSubmit = (event: Event) => {
  event.preventDefault()
  alert(JSON.stringify(form))
}

const onReset = (event: Event) => {
  event.preventDefault()
  // Reset our form values
  form.emel = ''
  form.katalaluan = ''
  // Trick to reset/clear native browser form validation state
  show.value = false
  nextTick(() => {
    show.value = true
  })
}
</script>


<style scoped>
a { text-decoration: none; }
</style>
```

* Simpan / **Save** fail **login.vue**

## Langkah 1.2: Uji Laman Login

* * Di ***Command Prompt*** taip kod seperti berikut untuk buka aplikasi Nuxt

```
npm run dev
```

* Di browser layari pautan berikut **http://localhost:3000/login**, berikut adalah contoh paparan

<img src="https://code.cloud-connect.asia/jdn/latihan-aplikasi-moden/uploads/583ad2e7c1c3dde9b56e58c87b817092/image.png" width=350>

# Langkah 2.0: Laman Daftar

## Langkah 2.1: Ubah Laman Daftar

* Di VS Code, buka fail **daftar.vue** di direktori **pages**, padam kod sedia ada, salin dan tampal kod berikut

```vue
<template>
  <BContainer fluid>
    <BRow align-h="center">
      <BCol alignSelf="center" lg=5>
        <br />
        <h1 style="text-align: center;">Pendaftaran</h1>
        <hr />
        <BForm @submit="onSubmit" @reset="onReset" v-if="show">
          <BFormGroup
            id="input-group-1"
            label="Nama:"
            label-for="input-1"
          >
            <BFormInput
              id="input-1"
              v-model="form.nama"
              placeholder="Masukkan nama penuh"
              required
            />
          </BFormGroup>

          <BFormGroup id="input-group-2" label="Emel:" label-for="input-2">
            <BFormInput id="input-2" v-model="form.emel" placeholder="Masukkan emel yang sah" required />
          </BFormGroup>
          <BFormGroup id="input-group-3" label="Alamat:" label-for="input-3">
            <BFormInput id="input-3" v-model="form.alamat" placeholder="Masukkan alamat" required />
          </BFormGroup>
          <BFormGroup id="input-group-4" label="Daerah:" label-for="input-4">
            <BFormSelect id="input-4" v-model="form.daerah" :options="daerah" required />
          </BFormGroup>
          <BFormGroup id="input-group-5" label="Negeri:" label-for="input-5">
            <BFormInput id="input-5" v-model="form.negeri" placeholder="Masukkan negeri" required />
          </BFormGroup>
          <hr />
          <BButton type="submit" variant="primary">Submit</BButton>
          <BButton type="reset" variant="danger">Reset</BButton>
        </BForm>

        <BCard class="mt-3" header="Form Data Result">
          <pre class="m-0">{{ form }}</pre>
        </BCard>
      </BCol>
    </BRow>
  </BContainer>
</template>

<script setup lang="ts">
const daerah = [
    {text: 'Pilih Daerah', value: null}, 'Kota Tinggi', 'Segamat', 'Johor Bahru']

const form = reactive({
  nama: '',
  emel: '',
  alamat: '',
  daerah: null,
  negeri: ''
})
const show = ref(true)

const onSubmit = (event: Event) => {
  event.preventDefault()
  alert(JSON.stringify(form))
}

const onReset = (event: Event) => {
  event.preventDefault()
  // Reset our form values
  form.nama = ''
  form.emel = ''
  form.alamat = ''
  form.daerah = null
  form.negeri = ''
  // Trick to reset/clear native browser form validation state
  show.value = false
  nextTick(() => {
    show.value = true
  })
}
</script>
```

* Simpan / **Save** fail **daftar.vue**

## Langkah 2.2: Uji Laman Daftar

* * Di ***Command Prompt*** taip kod seperti berikut untuk buka aplikasi Nuxt

```
npm run dev
```

* Di browser layari pautan berikut **http://localhost:3000/daftar**, berikut adalah contoh paparan

<img src="/uploads/ef27bd2f27c8cfc7378e7f05feb77a87/image.png" width=550>


