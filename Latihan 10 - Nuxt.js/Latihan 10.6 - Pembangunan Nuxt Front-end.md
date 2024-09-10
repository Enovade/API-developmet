[[_TOC_]]

# Latihan 10.6: Pembangunan Nuxt Front-end

Latihan ini adalah untuk menunjukkan pemahaman pembangunan **Nuxt Front-end** yang akan menggunakan **Nuxt Pages, Layouts, Components** yang diwujudkan dari latihan sebelum ini.

Latihan ini adalah sambungan dari latihan [Latihan 5: Nuxt Components](https://code.cloud-connect.asia/msp/akademi-cloud-connect/training-modules/pembangunan-aplikasi-moden/-/blob/master/Latihan%2011/Latihan%205%20-%20Nuxt%20Components.md)


# Langkah 1.0: Laman Login

## Langkah 1.1: Ubah Laman Login

* Di VS Code, buka fail **login.vue** di direktori **pages**, padam kod sedia ada, salin dan tampal kod berikut

```vue
<script setup lang="ts">
  definePageMeta({
    layout: false,
  })
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

<template>
  <div>
    <section class="bg-gray-50 dark:bg-gray-900">
      <div class="flex flex-col items-center justify-center px-6 py-8 mx-auto md:h-screen lg:py-0">
          <NuxtLink to="/">
            <a href="#" class="flex items-center mb-6 text-2xl font-semibold text-gray-900 dark:text-white">
                <img class="w-22 h-20 mr-2" src="https://padu.gov.my/_next/image?url=%2Fimages%2Fjata_negara.png&w=256&q=75" alt="logo">
            </a>
          </NuxtLink>
          <div class="w-full bg-white rounded-lg shadow dark:border md:mt-0 sm:max-w-md xl:p-0 dark:bg-gray-800 dark:border-gray-700">
              <div class="p-6 space-y-4 md:space-y-6 sm:p-8">
                  <h1 class="text-xl font-bold leading-tight tracking-tight text-gray-900 md:text-2xl dark:text-white">
                      Laman Login
                  </h1>
                  <form @submit="onSubmit" @reset="onReset" v-if="show" class="space-y-4 md:space-y-6">
                      <div>
                          <label for="email" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Emel</label>
                          <input type="email" v-model="form.emel" name="email" id="email" class="bg-gray-50 border border-gray-300 text-gray-900 rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="name@company.com" required="">
                      </div>
                      <div>
                          <label for="password" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Katalaluan</label>
                          <input type="password" v-model="form.katalaluan" name="password" id="password" placeholder="••••••••" class="bg-gray-50 border border-gray-300 text-gray-900 rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" required="">
                      </div>
                      <div class="flex items-center justify-between">
                          <div class="flex items-start">
                              <div class="flex items-center h-5">
                                <input id="remember" aria-describedby="remember" type="checkbox" class="w-4 h-4 border border-gray-300 rounded bg-gray-50 focus:ring-3 focus:ring-primary-300 dark:bg-gray-700 dark:border-gray-600 dark:focus:ring-primary-600 dark:ring-offset-gray-800" required="">
                              </div>
                              <div class="ml-3 text-sm">
                                <label for="remember" class="text-gray-500 dark:text-gray-300"><i>Remember me</i></label>
                              </div>
                          </div>
                          <a href="#" class="text-sm font-medium text-primary-600 hover:underline dark:text-primary-500">Terlupa Katalaluan?</a>
                      </div>
                      <button type="submit" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800">Hantar</button>
                      <button type="reset" class="focus:outline-none text-white bg-red-700 hover:bg-red-800 focus:ring-4 focus:ring-red-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2 dark:bg-red-600 dark:hover:bg-red-700 dark:focus:ring-red-900">Reset</button>
                      <p class="text-sm font-light text-gray-500 dark:text-gray-400">
                          Tiada akses? <a href="#" class="font-medium text-primary-600 hover:underline dark:text-primary-500">Daftar Sekarang</a>
                      </p>
                  </form>
              </div>
          </div>
      </div>
    </section>
  </div>
</template>

<style scoped></style>

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


