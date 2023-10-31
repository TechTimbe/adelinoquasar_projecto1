<template>
  <q-page class="flex flex-center">
    <div class="q-pa-md" style="max-width: 400px">

<q-form
  @submit="onSubmit"
  @reset="onReset"
  class="q-gutter-md"
>
  <q-input
    filled
    v-model="name"
    label="Seu nome *"
    hint="Nome e sobrenome"
    lazy-rules
    :rules="[ val => val && val.length > 0 || 'Por favor preencha dados']"
  />

  <q-input
    filled
    type="number"
    v-model="age"
    label="Sua idade *"
    lazy-rules
    :rules="[
      val => val !== null && val !== '' || 'Por favor insira sua idade',
      val => val > 0 && val < 100 || 'Por favor insira idade real'
    ]"
  />

  <!-- Codigo de Radio -->
    <div class="q-gutter-sm">
      <q-radio v-model="shape" val="Masculino" label="Masculino" />
      <q-radio v-model="shape" val="Feminino" label="Feminino" />
    </div>

  <!-- Codigo de CheckBox   -->
    <div class="q-gutter-sm">
      <q-checkbox
        v-model="customModel"
        color="secondary"
        label="Aceita nossos termos de condições?"
        true-value="Aceites"
        false-value="Não aceites"
      />
    </div>
  <div>
    <q-btn label="Enviar" type="submit" color="primary"/>
    <q-btn label="Recomeçar" type="reset" color="primary" flat class="q-ml-sm" />
  </div>
</q-form>
<div class="q-px-sm">
      O sexo selecionado é: <strong>{{ shape }}</strong>
    </div>
    <div class="q-px-sm">
      Termos de condições: <strong>'{{ customModel }}'</strong>
    </div>

</div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import { useQuasar } from 'quasar' //formulario
import { ref } from 'vue' // formulario e radio


export default defineComponent({
  setup () {
    const $q = useQuasar()
    const name = ref(null)
    const age = ref(null)
    const accept = ref(false)
  name: 'IndexPage'
  return {
      name,
      age,
      shape: ref('Masculino'),
      customModel: ref('Não aceites'),

      onSubmit () {
          $q.notify({
            color: 'green-4',
            textColor: 'Black',
            icon: 'cloud_done',
            message: 'Submitted'
          })
      },

      onReset () {
        name.value = null
        age.value = null
      }
    }
  }
})
</script>
