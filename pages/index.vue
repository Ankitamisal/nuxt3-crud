<template>
    <div class="flex sm:container">
        <div class=" bg-pink-100  mt-1 ">
            <input type="text"
                class="flex-auto ml-4 block w-30  px-4 mt-2 text-base font-normal text-gray-700 bg-white border border-solid border-gray-300 rounded-xl px-5 p-1 m-1 "
                placeholder="Search" @keyup="userFindByName(userName)" v-model="userName" id="userName"
                name="userName" />

            <table class=" border-1 m-2" id="list">
                <tr>
                    <th class="px-2 border-blue-400 rounded-lg border-2">Full Name</th>
                    <th class="px-2 border-blue-400 rounded-lg border-2">Phone Number</th>
                    <th class="px-2 border-blue-400 rounded-lg border-2">Email</th>
                    <th class="px-2 border-blue-400 rounded-lg border-2">Address</th>
                    <th class="px-4 border-blue-400 rounded-lg border-2" colspan="2">Action</th>

                </tr>

                <tr v-for="(user, index) in userFound" :key="user">


                    <td class="px-2 border-blue-400 rounded-lg border-2">{{ user.fname }}</td>
                    <td class="px-2 border-blue-400 rounded-lg border-2">{{ user.number }}</td>
                    <td class="px-2 border-blue-400 rounded-lg border-2">{{ user.email }}</td>
                    <td class="px-2 border-blue-400 rounded-lg border-2">{{ user.address }}</td>
                    <td class="border-2 rounded-lg  border-blue-400">
                        <button class="mx-3 rounded-lg bg-red-600 hover:bg-red-700 text-white w-20"
                            @click="userDelete(index)">
                            Delete
                        </button>
                    </td>
                    <td class="border-2 rounded-lg  border-blue-400">
                        <button class="mx-3 rounded-lg bg-green-600 hover:bg-green-600 text-white w-20"
                            @click="onEdit(index)">
                            Edit
                        </button>
                    </td>
                </tr>

            </table>
        </div>

        <div class=" bg-blue-200  my-5 mx-5 mb-20">
            <form @submit="formSubmit" class="">
                <table class="ml-5 m-2 sm:item-center">
                    <h2 id="formEditName" class="text-teal-900 text-xl font-bold pt-6">Add user</h2>
                    <hr />
                    <br />
                    <label class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300" for="fname">Full
                        name:</label>
                    <input type="text" id="fname"
                        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 peer border border-slate-400 "
                        @change="validationName" v-model="user.fname" />

                    <label for="number" class="block  text-sm font-medium text-gray-900 dark:text-gray-300">Phone
                        Number: </label>
                    <input type="number" id="number"
                        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 "
                        @change="validationMobile" v-model="user.number">

                    <label for="text" class="block text-sm font-medium text-gray-900 dark:text-gray-300">email </label>
                    <input type="email" id="email" required
                        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                        v-model="user.email" pattern=".+@globex\.com" @change="validationEmail">

                    <br />
                    <label for="address" id="address">Address</label>
                    <textarea name="address" id="address"
                        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg  block w-full p-4 dark:bg-gray-700 dark:border-gray-600 "
                        v-model="user.address">
                  </textarea>
                    <br />
                    <div>

                        <button id="submit"
                            class="form-group py-1 px-5 mr-5  bg-black hover:bg-blue-400 text-white font-bold text-center rounded-md mb-1"
                            type="submit" @click="formSubmit">Submit</button>
                        <button
                            class="py-1 px-5 bg-black hover:bg-blue-400 text-white font-bold text-center rounded-md mb-3"
                            type="reset" id="reset" @click="resetForm"> Reset </button>
                    </div>
                </table>
            </form>
            {{ showUsers() }}
        </div>
    </div>

    <!-- </aside>
</section>
</section> -->
</template>

<script>
export default {
    data() {
        return {

            isEdit: false,
            indexEdit: -1,
            userName: '',
            userEmail: '',
            userAddress: '',
            userFound: [],

            users: [],
            uniqueEmail: [],
            fname1: '',
            fname2: '',
            email1: '',
            email2: '',
            number1: '',
            number2: '',
            emailMatch: '/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/',
            user: {
                fname: '',
                number: '',
                email: '',
                address: '',
            },
        };
    },

    methods: {

        showUsers() {
            // this.users = JSON.parse(localStorage.getItem('selectedUser'))
            if (this.userName == "") {
                this.userFound = this.users;

            }

        },
        formSubmit(event) {
            event.preventDefault(event);
            console.log(this.user);
            if (this.user.fname == '' || this.user.email == '' || this.user.number == '' || this.user.address == '') {
                alert('please fill form')
                this.resetForm();
            }

            //unqiue email
            this.uniqueEmail = this.users.filter((e) => {
                if (e.email != this.user.email) {
                    console.log(e);
                } else {
                    if (this.isEdit === true) {
                        this.users[this.indexEdit] = this.user;
                    } else {
                        alert("Email Already Registered");
                        this.resetForm();
                    }
                }
            });

            if (this.isEdit == true) {
                this.users[this.indexEdit] = this.user;
                this.isEdit = false;
                this.indexEdit = -1;
                // confirm(' data Successfully Updated');
            } else {
                if (this.user.fname == '' || this.user.email == '' || this.user.number == '' || this.user.address == '') {
                    alert('please fill form')
                    this.resetForm();
                } else {

                    this.users.push(this.user);
                    // localStorage.setItem('selectedUser', JSON.stringify(this.users));
                    confirm('Data is successfully added');
                }
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

        userDelete(index) {
            if (confirm('you want to delet data ?')) {
                this.users.splice(index, 1)

            }

            const formHead = document.getElementById('formEditName');
            formHead.innerText = 'Add User';
            const myButton = document.getElementById('submit');
            myButton.innerText = 'Submit';
            this.resetForm();

        },
        onEdit(index) {
            document.getElementById("submit").innerHTML = 'Update'
            console.log(this.users[index]);
            // console.log(this.allUserData[this.index]);
            this.user.fname = this.users[index].fname;
            this.user.email = this.users[index].email;
            this.user.number = this.users[index].number;
            this.user.address = this.users[index].address;
            const formHead = document.getElementById('formEditName');
            formHead.innerText = 'Edit User';
            const myButton = document.getElementById('submit');
            myButton.innerText = 'Update';
            this.isEdit = true;
            this.indexEdit = index;
        },

        resetForm() {
            console.log("reset call");
            const formHead = document.getElementById('formEditName');
            formHead.innerText = 'Add User';
            const myButton = document.getElementById('submit');
            myButton.innerText = 'Submit';
            // indexOfEdit=-1;
            this.isEdit = false;
            this.user = {
                fname: '',
                email: '',
                number: '',
                address: '',
            };
        },

        userFindByName(userName) {
            console.log(userName);
            this.userFound = this.users.filter((e) => {

                //         // if(e.name == userName)
                //         if (e.fname.startsWith(userName)) {
                //             console.log(e);
                //             // if(e.name.startsWith(userName))
                //             return e;
                //             // alert("user Found" + e.firstName+ ""+e.lastName);
                //         }
                //     });
                //     console.log(this.userFound);
                // },

                this.address1 = userName.toLocaleLowerCase();
                console.log(this.address1);
                this.address2 = e.address.toLocaleLowerCase();
                this.fname1 = userName.toLocaleLowerCase();
                this.fname2 = e.fname.toLocaleLowerCase();
                this.email1 = userName.toLocaleLowerCase();
                this.email2 = e.email.toLocaleLowerCase();
                this.number1 = userName.toString();
                this.number2 = e.number.toString();
                if (this.address2.startsWith(this.address1) || this.fname2.startsWith(this.fname1) || this.email2.startsWith(this.email1) || this.number2.startsWith(this.number1)) {
                    console.log(e);
                    // alert("user found ")
                    return e;
                }
            });
            console.log(this.userFound);
        },

        // validationName() {
        //     if (!isNaN(this.user.fname == '')) {
        //         alert('enter name')
        //         this.ResetForm();
        //     } else {
        //         console.log(this.user.fname);
        //         // alert("Name is valid");
        //     }

        // },

        validationEmail() {
            // if (/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(this.userData.email)){
            this.emailMatch = /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/;
            // if(this.userData.email.matchAll(this.emailMatch)){
            if (this.emailMatch.test(this.user.email)) {
                // alert("Email is valid");
                // console.log("Email is valid");
            } else {
                alert("Email is Invalid");
                this.resetForm();
            }
        },
        validationMobile() {
            // Validation for Mobile
            // If x is Not a Number or less than 10 digit or greater than 9999999999
            if (isNaN(this.user.number) || this.user.number < 1000000000 || this.user.number > 9999999999) {
                alert("Mobile Number is Invalid");
                this.resetForm();
            } else {
                // alert("Mobile Number is valid");
            }
        },

    }
}
</script>
