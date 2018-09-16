<template>
  <div class="hello">
    <h1 class="ml-3">Contatos</h1>
    <div class="holder">
    
    <!-- Button trigger modal -->
    <button type="button" class="btn btn-primary ml-3 mb-3" data-toggle="modal" data-target="#contactModal">Novo contato</button>

    <!-- Modal -->
    <div class="modal fade" id="contactModal" tabindex="-1" role="dialog" aria-labelledby="contactModalLabel" aria-hidden="true">
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="contactModalLabel">Novo Contato</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <form>
              <div class="form-group">
                <label for="newName">Nome</label>
                <input type="text" class="form-control" id="newName" placeholder="Nome" v-model="newName">
              </div>
              <div class="form-group">
                <label for="newEmail">Email</label>
                <input type="text" class="form-control" id="newEmail" placeholder="Email" v-model="newEmail">
              </div>
            </form>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-danger" data-dismiss="modal">Cancelar</button>
            <button type="submit" class="btn btn-primary" v-on:click="saveContact()" data-dismiss="modal">Salvar</button>
          </div>
        </div>
      </div>
    </div>

    <table class="table table-striped table-condensed" cellspacing="0" cellpadding="0">
      <thead>
        <tr>
          <th>Nome</th>
          <th>Email</th>
          <th class="actions">Ações</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(contact, index) in contacts" :key='index'>
          <td>{{ contact.name }}</td>
          <td>{{ contact.email }}</td>
          <td>
            <button type="button" class="btn btn-warning btn-xs mr-3" v-b-modal.modal1 v-on:click="editEmployee(index)">Editar</button>
            <button type="button" class="btn btn-danger btn-xs" v-on:click="deleteEmployee(index)">Excluir</button>
          </td>
        </tr>
      </tbody>
      </table>

  

    </div>
  </div>
</template>

<script>
import contacts from '../static/contacts.json'
export default {
  name: 'Contacts',
  data(){
    return {
      newName: null,
      newEmail: null,
      contacts: contacts
    }
  },
  methods: {
    saveContact() {
      this.contacts.push({ name: this.newName.trim(), email: this.newName.trim() })
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
