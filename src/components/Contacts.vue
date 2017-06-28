<template>
    <div class="contacts">
        <div class="container">
            <table class="table">
                <thead>
                    <tr>
                        <th>Имя</th>
                        <th>email</th>
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

</style>
