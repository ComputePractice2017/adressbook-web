<template>
    <div class="contacts">
        <div class="container">
            <form class="form-inline">
                <label class="sr-only" for="inlineFormInput">Name</label>
                <input type="text" class="form-control mb-2 mr-sm-2 mb-sm-0" id="inlineFormInput" placeholder="Имя">
    
                <label class="sr-only" for="inlineFormInputGroup">Username</label>
                <div class="input-group mb-2 mr-sm-2 mb-sm-0">
                    <input type="text" class="form-control" id="inlineFormInputGroup" placeholder="Email">
                </div>
      
                <button type="submit" class="btn btn-primary">Добавить</button>
            </form>




            <table class="table">
                <thead>
                    <tr>
                        <th>Имя</th>
                        <th>Email</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="contact in contacts">
                        <td>{{contact.name}}</td>
                        <td>{{contact.email}}</td>
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
      ]
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
