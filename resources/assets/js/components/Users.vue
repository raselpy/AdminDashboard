<template>
    <div class="container">
        <div class="row mt-5">
          <div class="col-12">
            <div class="card">
               <!-- add new user -->
              <div class="card-header">
                <h3 class="card-title">Users Table</h3>
                <div class="card-tools">
                   <button class="btn btn-success" data-toggle="modal" data-target="#exampleModal">Add New <i class="fas fa-user-plus"></i></button>
                </div>
              </div>
              <!-- End new users -->

              <!-- /.card-header -->
              <div class="card-body table-responsive p-0">
                <table class="table table-hover">
                  <tr>
                    <th>ID</th>
                    <th>User</th>
                    <th>Email</th>
                    <th>Type</th>
                    <th>Modify</th>
                  </tr>
                  <tr>
                    <td>183</td>
                    <td>John Doe</td>
                    <td>11-7-2014</td>
                    <td><span class="tag tag-success">Approved</span></td>
                    <td>
                        <a href="#">
                            <i class="fas fa-edit indigo">Edit</i>
                        </a>
                        /
                        <a href="#">
                            <i class="fas fa-trash red">Update</i>
                        </a>
                    </td>
                  </tr>
                  
                </table>
              </div>
              <!-- /.card-body -->
            </div>
            <!-- /.card -->
          </div>
        </div><!-- /.row -->
        <!-- Modal -->
           
                <div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
                  <div class="modal-dialog" role="document">
                    <div class="modal-content">
                      <div class="modal-header">
                        <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
                        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                          <span aria-hidden="true">&times;</span>
                        </button>
                      </div>
                    <form @submit.prevent="CreateUser">
                      <div class="modal-body">
                        
                        <div class="form-group">
                          <label>Name</label>
                              <input v-model="form.name" type="text" name="name" placeholder="Enter Name" 
                                class="form-control" :class="{ 'is-invalid': form.errors.has('name') }">
                              <has-error :form="form" field="name"></has-error>
                        </div>

                        <div class="form-group">
                          <label>Email</label>
                              <input v-model="form.email" type="email" name="email" placeholder="Add Email" 
                                class="form-control" :class="{ 'is-invalid': form.errors.has('email') }">
                              <has-error :form="form" field="email"></has-error>
                        </div>

                        <div class="form-group">
                          <label>password</label>
                              <input v-model="form.password" type="password" name="password" placeholder="Enter Password" 
                                class="form-control" :class="{ 'is-invalid': form.errors.has('password') }">
                              <has-error :form="form" field="password"></has-error>
                        </div>

                        <div class="form-group">
                            <select name="type" v-model="form.type" id="type" class="form-control" :class="{
                            'is-invalid': form.errors.has('type') }">
                                <option value="">Select User Role</option>
                                <option value="admin">Admin</option>
                                <option value="user">Standard</option>
                                <option value="author">Author</option>
                            </select>
                            <has-error :form="form" field="type"></has-error>
                        </div>
                        <div class="form-group">
                          <label>BIO</label>
                              <textarea v-model="form.bio" type="text" name="bio" placeholder="Add Bio (Optional)" 
                                class="form-control" :class="{ 'is-invalid': form.errors.has('bio') }">
                                </textarea>
                              <has-error :form="form" field="bio"></has-error>
                        </div>




                      </div>
                      <div class="modal-footer">
                        <button type="button" class="btn btn-danger" data-dismiss="modal">Close</button>
                        <button type="submit" class="btn btn-primary">Create</button>
                      </div>
                    </form>  
                    </div>
                  </div>
                </div>
            
    </div>

</template>

<script>
    export default {
        data(){
            return{
                form : new Form({
                    name : '',
                    email : '',
                    password : '',
                    type : '',
                    bio : '',
                    photo : '',
                })
            }
        },
        methods:{
          CreateUser(){
            this.form.post('api/user')
          }
        },
        mounted() {
            console.log('Component mounted.')
        }
    }
</script>
