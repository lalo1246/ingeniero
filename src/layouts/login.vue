<template>
  <div class="q-pa-md">
    
    <div class="q-gutter-md row items-start">
      <q-img
        src="http://lamarfe.com.ar/wp-content/uploads/2019/07/logo-7.png"
        srcset="http://lamarfe.com.ar/wp-content/uploads/2019/07/logo-7.png 400w,
                http://lamarfe.com.ar/wp-content/uploads/2019/07/logo-7.png 800w,
                http://lamarfe.com.ar/wp-content/uploads/2019/07/logo-7.png 1200w,
                http://lamarfe.com.ar/wp-content/uploads/2019/07/logo-7.png 1600w"
        sizes="(max-width: 400px) 400w,
              (min-width: 400px) and (max-width: 800px) 800w,
              (min-width: 800px) and (max-width: 1200px) 1200w,
              (min-width: 1200px) 1600w"
        style="max-width: 100%"
      >
      </q-img>
  </div>
    <q-form
        @submit="onSubmit"
        @reset="onReset"
        class="q-gutter-md"
      >
      <q-input
        filled
        v-model="name"
        label="Your name *"
        hint="Name and surname"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Please type something']"
      />

      <q-input
        filled
        type="number"
        v-model="age"
        label="Your age *"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'Please type your age',
          val => val > 0 && val < 100 || 'Please type a real age'
        ]"
      />

      <q-toggle v-model="accept" label="I accept the license and terms" />

      <div>
        <q-btn to="/play" label="Submit" type="submit" color="primary"/>
        <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
    </q-form>

  </div>
</template>
<script>
export default {

}
</script>