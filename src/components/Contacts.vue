<template>
    <div class="contacts">
        <div class="container">
            <form class="form">
                <input class="form-control" type="text" placeholder="Поиск" id="example-text-input" v-model="search">
            </form>

            <table class="table">
                <thead>
                    <tr>
                        <th>Имя</th>
                        <th>Email</th>
                        <th></th>
                    </tr>
                </thead>
                <tbody v-for="contact in contactList">
                    <tr>
                        <td>{{contact.name}}</td>
                        <td>{{contact.email}}</td>
                        <td>
                            <button v-on:click="editContact(contact)" v-if="!edit" type="button" class="btn btn-warning">Изменить</button>
                            <button v-on:click="deleteContact(contact)" v-if="!edit" type="button" class="btn btn-danger">Удалить</button>
                        </td>
                    </tr>
                </tbody>
            </table>

            <form class="form-inline">
                <label class="sr-only" for="inlineFormInput">Name</label>
                <input type="text" v-model="newcontact.name" class="form-control mb-2 mr-sm-2 mb-sm-0" id="inlineFormInput" placeholder="Имя">
    
                <label class="sr-only" for="inlineFormInputGroup">Username</label>
                <div class="input-group mb-2 mr-sm-2 mb-sm-0">
                    <input type="email" v-model="newcontact.email"  class="form-control" id="inlineFormInputGroup" placeholder="Email">
                </div>
      
                <button v-on:click="addNewContact" v-if="!edit" type="button" class="btn btn-primary">Добавить</button>
                <button v-on:click="endEdit" v-if="edit" type="button" class="btn btn-danger">Сохранить</button>
            </form>
        </div>  
    </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      contacts: [
        {
          'id': 1,
          'name': 'Alice',
          'email': 'alice@company.org'
        },
        {
          'id': 2,
          'name': 'Bob',
          'email': 'bob@company.org'
        }
      ],
      edit: false,
      newcontact: {
        'name': '',
        'email': ''
      },
      search: ''
    }
  },
  computed: {
    contactList: function () {
      var search = this.search
      var filterFn = function (item) {
        return item.name.includes(search) || item.email.includes(search)
      }
      if (this.search !== '') {
        return this.contacts.filter(filterFn)
      }
      return this.contacts
    }
  },
  methods: {
    addNewContact: function () {
      var obj = {
        'name': '',
        'email': ''
      }
      obj.name = this.newcontact.name
      obj.email = this.newcontact.email
      this.contacts.push(obj)
    },
    editContact: function (obj) {
      this.edit = true
      this.newcontact = obj
    },
    endEdit: function () {
      this.edit = false
      var obj = {
        'name': '',
        'email': ''
      }
      this.newcontact = obj
    },
    deleteContact: function (obj) {
      var eq = function (input) {
        return input.name === obj.name && input.email === obj.email
      }
      var index = this.contacts.findIndex(eq)
      if (index > -1) {
        this.contacts.splice(index, 1)
      }
    }
  }
}
</script>

<style>
.form {
    margin-top: 20px;
    margin-bottom: 20px;
}
</style>
