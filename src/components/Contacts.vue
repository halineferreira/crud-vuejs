<template>
  <div>
    <h1>Contatos</h1>
    <b-form inline>
      <b-input class="mb-2 mr-sm-2 mb-sm-0" id="newName" placeholder="Name" v-model="newName"/>
      <b-input class="mb-2 mr-sm-2 mb-sm-0" id="newEmail" placeholder="Email" v-model="newEmail"/>
      <b-button variant="primary" v-on:click="addContact()">Inserir</b-button>
    </b-form>
    <br>
    <table class="table table-striped table-condensed" cellspacing="0" cellpadding="0">
      <thead>
        <tr>
          <th>Nome</th>
          <th>Email</th>
          <th class="actions">Ações</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(contact, index) in contacts" :key="index">
          <td>{{ contact.name }}</td>
          <td>{{ contact.email }}</td>
          <td>
            <button type="button" class="btn btn-warning btn-xs mr-2" v-b-modal.modal1 v-on:click="editContact(index)">Editar</button>
            <button type="button" class="btn btn-danger btn-xs" v-on:click="deleteContact(index)">Excluir</button>
          </td>
        </tr>
      </tbody>
    </table>

    <b-modal id="modal1" title="Editar funcionário" @ok="saveContact(index)">
      <input type="text" class="form-control" name="name" id="name" placeholder="Name"><br>
      <input type="email" class="form-control" name="email" id="email" placeholder="Email">
    </b-modal>
  </div>
  
</template>

<script>
import contacts from '../static/contacts.json'
export default {

  data () {
    return {
      index: null,
      newName: null,
      newEmail: null,
      contacts: contacts
    }
  },
  methods: {
    addContact: function () {
      if (!this.newName.trim() || !this.newEmail.trim()) { return }
      this.contacts.push(
        { name: this.newName.trim(), email: this.newEmail.trim() }
      )
      this.newName = ''
      this.newEmail = ''
    },
    deleteContact: function (index) {
      contacts.splice(index, 1)
    },
    editContact: function (index) {
      // alert(contacts[index].name)
      this.index = index
      document.querySelector('input[name=name]').value = contacts[index].name
      document.querySelector('input[name=email]').value = contacts[index].email
    },
    saveContact: function () {
      contacts[this.index].name = document.querySelector('input[name=name]').value
      contacts[this.index].email = document.querySelector('input[name=email]').value
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>