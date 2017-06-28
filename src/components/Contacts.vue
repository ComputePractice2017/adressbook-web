<template>
    <div class="contacts">
        <div class="container">
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

            <table class="table">
                <thead>
                    <tr>
                        <th>Имя</th>
                        <th>Email</th>
                        <th></th>
                    </tr>
                </thead>
                <tbody v-for="contact in contacts">
                    <tr>
                        <td>{{contact.name}}</td>
                        <td>{{contact.email}}</td>
                        <td><button v-on:click="editContact(contact)" v-if="!edit" type="button" class="btn btn-warning">Изменить</button></td>
                    </tr>
                </tbody>
            </table>
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
      }
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
    }
  }
}
</script>

<style>
.form-inline {
    margin-top: 20px;
    margin-bottom: 20px;
}
</style>
