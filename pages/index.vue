<template>
<Add />
<main class="flex justify-center ">
    <div class="w-3/2">

        <form @submit="formSubmit" class="bg-gray-100 border-2 px-12 bg-gradient-to-r from-cyan-300 to-blue-200">
            <table>

                <h2 class="text-teal-900 text-xl font-bold pt-6">Information Form</h2>
                <hr />
                <br />

                <NuxtLink v-slot="{ navigate }" to="/Add" target="_blank" custom>
                    <button @click="navigate" class="bg-green-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
                        Add
                    </button>
                </NuxtLink><br><br>
                <label class="pt-10 py-10 " for="firstname">Full name:</label><br />
                <input type="text" v-model="user.fname" id="firstname" name="fname" placeholder="Enter your Full name" /><br /><br />
                <label for="address"> address: </label><br />
                <input type="text" v-model="user.address" id="address" name="address" placeholder="Enter your address" />
                <br /><br />
                <label for="number">Phone Number: </label><br />
                <input type="number" v-model="user.number" id="number" name="number" placeholder="Enter your number" />
                <br /><br />
                <label for="text">Email: </label><br />
                <input type="email" v-model="user.email" id="email" name="email" placeholder="Enter your Email-id" />
                <br /><br />
                <div>
                    <button class="py-1 px-5 mr-5 bg-black hover:bg-cyan-500 shadow-lg shadow-cyan-500/50 text-white font-bold text-center rounded-md mb-3" type="submit" @click="formSubmit" id="btnsub"> Submit </button>
                    <button class="py-1 px-5 bg-black hover:bg-cyan-500 shadow-lg shadow-cyan-500/50 text-white font-bold text-center rounded-md mb-3" type="reset"> Reset </button>
                    <div>

                    </div>
                </div>
            </table>

        </form>
    </div>
    <br>
    <table class="list">

        <!-- <div class="border-2 border-gray-200 rounded">
            <input type="text" class="px-4 py-2" placeholder="Search...">
            <button class="px-4 text-white bg-gray-600 border-l " @click="userFindByName(Name)">
                Search
            </button>
        </div> -->
            
<div class="flex items-center justify-center ">
    <div class="flex border-2 border-gray-200 rounded">
        <input type="text" class="px-4 py-2 w-80" placeholder="Search...">
        <button class="px-4 text-white bg-gray-600 border-l " @click="userFindByName()">
            Search
        </button>
    </div>
</div>
        <div class="flex items-center justify-center w:3/2">



            <tr>

                <!-- <th class="px-4 border-black rounded-lg border-2">id</th> -->
                <th class="px-8 border-blue-400 rounded-lg border-1">Full Name</th>
                <!-- <th class="px-4 border-blue-400 rounded-lg border-4">Last Name</th> -->
                <th class="px-8 border-blue-400 rounded-lg border-1">Address</th>
                <th class="px-8 border-blue-400 rounded-lg border-1">Email</th>
                <th class="px-8 border-blue-400 rounded-lg border-1">Contact No</th>
                <th class="px-8 border-blue-400 rounded-lg border-1">Action</th>
          
            <tr v-for="(item,index) in users" v-bind:index="index" :key="item">
                <!-- <td class="px-4 border-black rounded-lg border-2">{{item.id=i+1}}</td> -->
                <td class="px-2 border-blue-400 rounded-lg border-2">{{item.fname}}</td>
                <!-- <td class="px-4 border-blue-400 rounded-lg border-4">{{item.lastname}}</td> -->
                <td class="px-2 border-blue-400 rounded-lg border-2">{{item.address}}</td>
                <td class="px-2 border-blue-400 rounded-lg border-2">{{item.email}}</td>
                <td class="px-2 border-blue-400 rounded-lg border-2">{{item.number}}</td>
                <td class="px-2 border-blue-400 rounded-lg border-2">{{item.Action}}
                    <button class="mx-3 rounded-lg bg-red-600 hover:bg-red-700 text-white w-20" @click="userDelete(index)">
                        Delete
                    </button>
                    <button class="mx-3 rounded-lg bg-green-600 hover:bg-green-600 text-white w-20" @click="onEdit(index)">
                        Edit
                    </button>
                </td>
                  </tr>
            </tr>
        </div>
    </table>

</main>
</template>

<script>
export default {
    data() {
        return {

            isEdit: false,
            indexEdit: -1,
            Name: '',
            userFound: [],
            users: [],
            allUserData : [],
            user: {
                fname: '',
                // lastname: '',
                address: '',
                email: '',
                number: '',
            },
            search: '',
        };

    },
    methods: {
        formSubmit(event) {
            event.preventDefault();
            document.getElementById("btnsub").innerHTML = 'Submit'
            if (this.isEdit == true) {
                this.users[this.indexEdit] = this.user;
                this.isEdit = false;
                this.indexEdit = -1;
                alert('Successfully Updated')
            } else {
                this.users.push(this.user);
                alert('Data Added')
            }
            this.user = {
                fname: '',
                lastname: '',
                address: '',
                email: '',
                number: ''
            };
        },
        onReset(event) {
            event.preventDefault();
            this.form.email = "";
            this.form.name = "";
            this.form.address = "";
            this.form.contact = "";
            this.form.city = ""
        },
        userDelete(index) {
            this.users.splice(index, 1)
        },
        onEdit(index) {
            document.getElementById("btnsub").innerHTML = 'Update'
            this.user.fname = this.users[index].fname;
            // this.user.lastname=this.users[index].lastname;
            this.user.address = this.users[index].address;
            this.user.email = this.users[index].email;
            this.user.number = this.users[index].number;
            this.isEdit = true;
            this.indexEdit = index;
        },

        userFindByName(Name) {
            console.log(Name);
            this.userFound = this.allUserData.filter((e) => {
                if (e.fname == Name) {
                    console.log(e);
                    return e;
                    // alert("user Found" + e.firstName+ ""+e.lastName);
                    alert('not found')
                }
            });
            console.log(this.userFound)
            alert('user is here')

        }

    }
}
</script>
