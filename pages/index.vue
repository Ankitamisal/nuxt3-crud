<template>
<main class="flex justify-center w-3/2 ">
    <div>
         <!-- <h1 id="formName" class="text-blue Sm:text-3xl item-center font-bold ml-8">Add User</h1> -->
        <form @submit="formSubmit" class="bg-gray-100 border-blue-400 rounded-lg border-2 px-12">
            <table>
                <h2 id="formEditName" class="text-teal-900 text-xl font-bold pt-6">Add user</h2>
                <hr />
                <br />
                <label class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300" for="fname">Full name:</label>
                <input type="text" id="fname" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 " v-model="user.fname" required>
            
                <label for="number" class="block  text-sm font-medium text-gray-900 dark:text-gray-300">Phone Number: </label>
                <input type="number" id="number" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 "  maxlength="9" v-model="user.number" required>
                <label for="text" class="block text-sm font-medium text-gray-900 dark:text-gray-300">email </label>
                <input type="email" id="email" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="user.email" required>
                <label for="address" id="address">Address</label>
                <textarea name="address" id="address"  class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg  block w-full p-4 dark:bg-gray-700 dark:border-gray-600 " v-model="user.address" required></textarea><br/>
                <div>
                    <button  id="submit" class="py-1 px-5 mr-5  bg-black hover:bg-blue-400 text-white font-bold text-center rounded-md mb-1" type="submit" @click="formSubmit" > Submit </button>
                    <button class="py-1 px-5 bg-black hover:bg-blue-400 text-white font-bold text-center rounded-md mb-3" type="reset"> Reset </button>
                </div>
            </table>
        </form>
        <br>
        <input type="search" class="form-control relative flex-auto min-w-0 block w-50 px-3 py-1.5 text-base font-normal text-gray-700 bg-white border border-solid border-gray-300 rounded " placeholder="Search" @click="userFindByName(userName)" v-model="userName" id="userName" name="userName"/> <br>
       
      <button class="btn inline-block px-6 py-2 border-2 border-blue-600 text-blue-600 font-medium text-xs leading-tight uppercase rounded hover:bg-black " type="button">
      Search</button>
     <!-- <input type="text" id="myInput" @click="myFunction" placeholder="Search for names.." title="Type in a name"> -->
        <br/>
        <br/>
        <table class="list" id="list">
            <div class="w:1/3">
            <tr>
                <!-- <th class="px-4 border-black rounded-lg border-2">id</th> -->
                <th class="px-4 border-blue-400 rounded-lg border-4">Full Name</th>
                <th class="px-4 border-blue-400 rounded-lg border-4">Phone Number</th>
                <th class="px-4 border-blue-400 rounded-lg border-4">Email</th>
                <th class="px-4 border-blue-400 rounded-lg border-4">Address</th>
              
            </tr>
            <tr v-for="(item,index) in users" v-bind:index="index" :key="item">
                <!-- <td class="px-4 border-black rounded-lg border-2">{{item.id=i+1}}</td> -->
                <td class="px-4 border-blue-400 rounded-lg border-4">{{item.fname}}</td>
                <td class="px-4 border-blue-400 rounded-lg border-4">{{item.number}}</td>
                <td class="px-4 border-blue-400 rounded-lg border-4">{{item.email}}</td>
                <td class="px-4 border-blue-400 rounded-lg border-4">{{item.address}}</td>
                    <button  class="mx-3 rounded-lg bg-red-600 hover:bg-red-700 text-white w-20" @click="userDelete(index)">
                        Delete
                    </button>
                    <button class="mx-3 rounded-lg bg-green-600 hover:bg-green-600 text-white w-20" @click="onEdit(index)">
                        Edit
                    </button>
                
            </tr>
         </div> 
        </table>
         
    </div>
    <div>
           <table class="list" id="list">
            <div class="w:1/3">
            <tr>
                <!-- <th class="px-4 border-black rounded-lg border-2">id</th> -->
                <th class="px-4 border-blue-400 rounded-lg border-4">Full Name</th>
                <th class="px-4 border-blue-400 rounded-lg border-4">Phone Number</th>
                <th class="px-4 border-blue-400 rounded-lg border-4">Email</th>
                <th class="px-4 border-blue-400 rounded-lg border-4">Address</th>
              
            </tr>
            <tr v-for="item in userFound" :key="item">
                <!-- <td class="px-4 border-black rounded-lg border-2">{{item.id=i+1}}</td> -->
                <td class="px-4 border-blue-400 rounded-lg border-4">{{item.fname}}</td>
                <td class="px-4 border-blue-400 rounded-lg border-4">{{item.number}}</td>
                <td class="px-4 border-blue-400 rounded-lg border-4">{{item.email}}</td>
                <td class="px-4 border-blue-400 rounded-lg border-4">{{item.address}}</td>
                
            </tr>
         </div> 
         
        </table>
  </div>
</main>
</template>
<script>
export default {
    data() {
        return {
            search : '',
            isEdit: false,
            indexEdit: -1,
            userName:'',
            userEmail:'',
            userAddress:'',
            userFound:[],
            users:[],
             fname1:'',
            fname2:'',
            user: {
                fname: '',
                number: '',
                email: '',
                address: '',
            },
        };
    },
    methods: {
        formSubmit(event) {
            event.preventDefault(event);
            console.log(this.user);
            if (this.isEdit == true) {
                this.users[this.indexEdit] = this.user;
                this.isEdit = false;
                this.indexEdit = -1;
                 confirm(' data Successfully Updated');
            } else {
                this.users.push(this.user);
                confirm('Data is successfully added');
            }
            this.user = {
                fname: '',
                number: '',
                email: '',
                address: '',
            };
             console.log(" User Form Values", this.users);
                const formHead = document.getElementById('formEditName');
            formHead.innerText = 'Add User';
            const myButton = document.getElementById('submit');
            myButton.innerText = 'Submit';
        },
        // onReset(event) {
        //     event.preventDefault();
        //     this.form.email = "";
        //     this.form.name = "";
        //     this.form.address = "";
        //     this.form.contact = "";
        //     this.form.city=""
        userDelete(index) {
            if(confirm('you want to delet data ?')){
            this.users.splice(index, 1)
            }
              const formHead = document.getElementById('formEditName');
            formHead.innerText = 'Add User';
            const myButton = document.getElementById('submit');
            myButton.innerText = 'Submit';
        },
        onEdit(index) {
            document.getElementById("submit").innerHTML='Update'
            this.user.fname = this.users[index].fname;
            this.user.number = this.users[index].number;
            this.user.email = this.users[index].email;
            this.user.address = this.users[index].address;
            this.isEdit = true;
            this.indexEdit = index;

             const formHead = document.getElementById('formEditName');
            formHead.innerText = 'Edit User';
            const myButton = document.getElementById('submit');
            myButton.innerText = 'Update';
            this.isEdit=true;
            this.indexEdit = index;
        },
        
     userFindByName(userName){         
            console.log(userName);
            this.userFound = this.users.filter((e) => {
                // if(e.name == userName)
                if(e.fname.startsWith(userName)){
                    console.log(e);
                    // if(e.name.startsWith(userName))
                    return e;
                    // alert("user Found" + e.firstName+ ""+e.lastName);
                }
            }); 
            console.log(this.userFound);           
        },
    }
}
</script>