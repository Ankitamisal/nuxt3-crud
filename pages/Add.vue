<template>
<section class=" h-screen m-auto  mt-3">
           <div class="text-center">
               <form action="" class=" mx-auto   rounded-md p-10 flex flex-col flex sm:justify-content">
                    <div class="p-16 flex flex-col border-2 bg-white rounded-lg  border-red-50">
                        
                        <div class="p-4  border-gray-800 rounded">
                            <input type="text" placeholder="Full Name" class=" rounded-sm border-2 border-red-100 placeholder:text-center placeholder:text-lg  p-1">
                        </div>
                         <div class="p-2  border-gray-800 rounded">
                        <input type="text" placeholder="Address" class=" border-2 border-gray-800 rounded placeholder:text-center placeholder:text-lg  p-2 mt-3">
                        </div>
                        <div  class="p-2  border-gray-800 rounded">
                            <input type="email" placeholder="Email Address" class=" rounded-sm border-2 border-red-100 placeholder:text-center placeholder:text-lg  p-1">
                        </div>
                        <div  class="p-2  border-gray-800 rounded">
                        <input type="text" placeholder="Phone no +88019...." class=" border-[0.5px] border-gray-800 rounded placeholder:text-center focus:outline-none p-2 mt-3">
                    </div>
                    <div class="p-2  border-gray-800 rounded">
                        <button type="submit" class=" bg-gray-600 hover:bg-emerald-600 text-white text-2xl p-2 rounded-xl mt-3">Submit</button>
                    </div>
            </div>
             </form>
                    </div>
                     <table class="list" id="list">
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
                    <button class="mx-3 rounded-lg bg-red-600 hover:bg-red-700 text-white w-20" @click="userDelete(index)">
                        Delete
                    </button>
                    <button class="mx-3 rounded-lg bg-green-600 hover:bg-green-600 text-white w-20" @click="onEdit(index)">
                        Edit
                    </button>
                
            </tr>
           
        </table>
            
        </section>            <table class="list" id="list">
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
     \
            </tr>
           
        </table>
       </template>