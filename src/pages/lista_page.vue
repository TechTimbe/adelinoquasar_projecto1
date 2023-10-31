<template>
  <q-page class="bg-grey-3 column">
    <div class="row q-pa-sm bd-primary">
      <q-input 
      v-model="novatarefa" 
      @keyup.enter="addtarefa"
      class="col"
      bg-color="white"
      filled 
      bottom-slots
      placeholder="Adicione tarefa"
      dense>
        <template v-slot:append>
          <q-btn
          @click="addtarefa"
           round
          dense 
          flat 
          icon="add" />
        </template>
      </q-input>
  </div>
    <q-list 
    separator
    bordered
    class="bg-white">
      <q-item 
      v-for="tarefa in tarefas"
      :key="tarefa.title"
      @click="tarefa.done = !tarefa.done"
      :class="{'done bg-blue-1' : tarefa.done}"
      clickable
      v-ripple>
        <q-item-section avatar>
          <q-checkbox 
          v-model="tarefa.done"
          class="no-pointer-events"
          color="primary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ tarefa.title }}</q-item-label>
        </q-item-section>
        <q-item-section
        v-if=" tarefa.done"
        side
        >
        <q-btn 
        @click.stop="deleteTarefa(index)"
        flat round dense color="primary" icon="delete" />
        </q-item-section>
      </q-item>
    </q-list>
    <div 
    v-if="!tarefas.length"
    class="no-tarefas absolute-center">
      <q-icon
      name="check"
      size="100px"
      color="primary"/>
      <div class="text-h5 text-primary text-center">
        Sem Tarefas
      </div>
    </div>
  </q-page>
</template>

<script>
export default{
  data(){
    return{
      novatarefas: '',
      tarefas:[
       
      ]

    }
  },
  methods:{
    deleteTarefa(index){
      this.$q.dialog({
        title: 'Apagar Tarefa',
        message: 'Tens certeza que deseja apagar!',
        cancel: 'Não',
        persistent: 'Sim'
      }).onOk(() => {
        this.tarefas.splice(index, 1)
        this.$q.notify('Tarefa apagada')
      })
    },
    addtarefa(){
      this.tarefas.push({
        title: this.novatarefa,
        done: false
      })
      this.novatarefa = ''
    }
  }
}

</script>

<style lang ="scss">
.done{
  .q-item__label {
text-decoration: line-through;
color: #bbb;
  }
}
.no-tarefas{
  opacity: 0.5;

}


</style>
