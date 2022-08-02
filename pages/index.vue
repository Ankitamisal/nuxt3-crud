<template>
<section class="relative">
    <content class="flex  p-10 w-30 mt-5">
        <input type="search" class="form-control relative flex-auto min-w-0 block w-50 px-3 py-1.5 text-base font-normal text-gray-700 bg-white border border-solid border-gray-300 rounded " placeholder="Search" @keyup="userFindByName(userName)" v-model="userName" id="userName" name="userName" />

    </content>
    <div class="flex float-left ml-20">
        <table class="" id="list">
            <tr>
                <!-- <th class="px-4 border-black rounded-lg border-2">id</th> -->
                <th class="px-2 border-blue-400 rounded-lg border-2">Full Name</th>
                <th class="px-2 border-blue-400 rounded-lg border-2">Phone Number</th>
                <th class="px-2 border-blue-400 rounded-lg border-2">Email</th>
                <th class="px-2 border-blue-400 rounded-lg border-2">Address</th>
                <th class="px-4 border-blue-400 rounded-lg border-2">Action</th>

            </tr>
            <tr v-for="(item,index) in users" v-bind:index="index" :key="item">
                <!-- <td class="px-4 border-black rounded-lg border-2">{{item.id=i+1}}</td> -->
                <td class="px-2 border-blue-400 rounded-lg border-2">{{item.fname}}</td>
                <td class="px-2 border-blue-400 rounded-lg border-2">{{item.number}}</td>
                <td class="px-2 border-blue-400 rounded-lg border-2">{{item.email}}</td>
                <td class="px-2 border-blue-400 rounded-lg border-2">{{item.address}}</td>
                <td>
                    <button class="mx-3 rounded-lg bg-red-600 hover:bg-red-700 text-white w-20" @click="userDelete(index)">
                        Delete
                    </button>
                </td>
                <td>
                    <button class="mx-3 rounded-lg bg-green-600 hover:bg-green-600 text-white w-20" @click="onEdit(index)">
                        Edit
                    </button>
                </td>
            </tr>

        </table>
    </div>
</section>
<div>
    <!-- <h1 id="formName" class="text-blue Sm:text-3xl item-center font-bold ml-8">Add User</h1> -->
    <form @submit="formSubmit" class="form-control flex justify-center bg-gray-100 border-blue-400 rounded-lg border-2  px-20 ml-20 mr-20 mb-20 float-right">
        <table>
            <h2 id="formEditName" class="text-teal-900 text-xl font-bold pt-6">Add user</h2>
            <hr />
            <br />
            <label class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300" for="fname">Full name:</label>
            <input type="text" id="fname" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 peer border border-slate-400 " @change="validationName" v-model="user.fname" />

            <label for="number" class="block  text-sm font-medium text-gray-900 dark:text-gray-300">Phone Number: </label>
            <input type="number" id="number" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 " @change="validationMobile" v-model="user.number">
           

            <label for="text" class="block text-sm font-medium text-gray-900 dark:text-gray-300">email </label>
            <input type="email" id="email" required class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="user.email" pattern=".+@globex\.com" @change="validationEmail">

            <br />
            <label for="address" id="address">Address</label>
            <textarea name="address" id="address" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg  block w-full p-4 dark:bg-gray-700 dark:border-gray-600 " v-model="user.address" aria-required="true">
                  </textarea>
            <br />
            <div>

                <button id="submit" class="form-group py-1 px-5 mr-5  bg-black hover:bg-blue-400 text-white font-bold text-center rounded-md mb-1" type="submit" @click="formSubmit"> Submit </button>
                <button class="py-1 px-5 bg-black hover:bg-blue-400 text-white font-bold text-center rounded-md mb-3" type="reset" @click="ResetForm"> Reset </button>
            </div>
        </table>
    </form>
</div>
<br>

<!-- <input type="text" id="myInput" @click="myFunction" placeholder="Search for names.." title="Type in a name"> -->
<br />
<br />

<div class="flex float-left ml-20 mb-20">

    <table class="list " id="list">
        <div class=" ">
            <tr>
                <!-- <th class="px-4 border-black rounded-lg border-2">id</th> -->
                <th class="px-4 border-blue-400 rounded-lg border-2">Full Name</th>
                <th class="px-4 border-blue-400 rounded-lg border-2">Phone Number</th>
                <th class="px-4 border-blue-400 rounded-lg border-2">Email</th>
                <th class="px-4 border-blue-400 rounded-lg border-2">Address</th>

            </tr>
            <tr v-for="item in userFound" :key="item">
                <!-- <td class="px-4 border-black rounded-lg border-2">{{item.id=i+1}}</td> -->
                <td class="px-4 border-blue-400 rounded-lg border-2">{{item.fname}}</td>
                <td class="px-4 border-blue-400 rounded-lg border-2">{{item.number}}</td>
                <td class="px-4 border-blue-400 rounded-lg border-2">{{item.email}}</td>
                <td class="px-4 border-blue-400 rounded-lg border-2">{{item.address}}</td>

            </tr>
        </div>

    </table>
</div>
</template>

<script>
export default {
    data() {
        return {
            search: '',
            isEdit: false,
            indexEdit: -1,
            email: '',
            msg: [],
            userName: '',
            userEmail: '',
            userAddress: '',
            userFound: [],
            userNumber: [],
            users: [],
            uniqueEmail: [],
            fname1: '',
            fname2: '',
            email1: '',
            email2: '',
            number1: '',
            number2: '',

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

            // if (this.user.email == '') {
            //     alert("Please enter unique Email Id")
            // } else {

            //     this.allUserData.push(this.user);
            // }

            console.log(" User Form Values", this.users);
            const formHead = document.getElementById('formEditName');
            formHead.innerText = 'Add User';
            const myButton = document.getElementById('submit');
            myButton.innerText = 'Submit';
        },
        //     onReset(event) {
        //         event.preventDefault();
        //         this.form.email = "";
        //         this.form.name = "";
        //         this.form.address = "";
        //         this.form.contact = "";
        //         this.form.city=""
        // }
        userDelete(index) {
            if (confirm('you want to delet data ?')) {
                this.users.splice(index, 1)
            }
            const formHead = document.getElementById('formEditName');
            formHead.innerText = 'Add User';
            const myButton = document.getElementById('submit');
            myButton.innerText = 'Submit';
        },
        onEdit(index) {
            document.getElementById("submit").innerHTML = 'Update'
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
            this.isEdit = true;
            this.indexEdit = index;
        },
        ResetForm() {
            console.log("reset call");
            const myButton = document.getElementById('submit');
            myButton.innerText = 'Submit';
            // indexOfEdit=-1;
            this.isEdit = false;
            this.users = {
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

                this.address1 = userAddress.toLocaleLowerCase();
                console.log(this.address1);
                this.address2 = e.address.toLocaleLowerCase();
                this.fname1 = userAddress.toLocaleLowerCase();
                this.fname2 = e.fname.toLocaleLowerCase();
                this.email1 = userAddress.toLocaleLowerCase();
                this.email2 = e.email.toLocaleLowerCase();
                this.number1 = userAddress.toString();
                this.number2 = e.number.toString();
                if (this.address2.startsWith(this.address1) || this.fname2.startsWith(this.fname1) || this.email2.startsWith(this.email1) || this.mobile2.startsWith(this.mobile1)) {
                    console.log(e);
                    return e;
                }
            });
            console.log(this.userFound);
        },
        // validateEmail(value) {
        //     if (/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(value)) {
        //         this.msg['email'] = '';
        //     } else {
        //         this.msg['email'] = 'Please enter a valid email address';
        //     }
        // }
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
                this.ResetForm();
            }
        },
          validationMobile(){
            // Validation for Mobile
            // If x is Not a Number or less than 10 digit or greater than 9999999999
            if (isNaN(this.user.number) || this.user.number < 1000000000 || this.user.number > 9999999999) {
                alert("Mobile Number is Invalid");
                this.ResetForm();
            } else {
                // alert("Mobile Number is valid");
            }
        },

    }
}
</script>
