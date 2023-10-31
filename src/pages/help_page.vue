<template>
  <q-page class="q-pa-lg">

<h5 class="q-mt-none">Ajuda</h5>
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Eum esse error consequuntur, animi placeat fugiat debitis dolores in quidem, vero enim, libero perspiciatis aliquam rem perferendis praesentium similique nulla eveniet.</p>
<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto distinctio et provident deleniti repellat exercitationem tempora temporibus ab, quibusdam, nostrum ut ratione inventore laudantium hic, recusandae quasi saepe incidunt quo?</p>
<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto eos pariatur dolore veniam nisi neque minima aperiam ad amet consequuntur facere libero ex ipsam assumenda adipisci placeat commodi, saepe molestiae.</p>
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
