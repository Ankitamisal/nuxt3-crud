<template>
    <div class="">
        <h1 class="text-center my-2">Resume Generator</h1>
        <p class="text-center">By LearnCodeWith Durgesh</p>
    </div>
    <h3>Personal Information</h3>
    <form class="w-full max-w-lg">
        <div class="flex">
        <div class=" flex-wrap flex-1 w-64 -mx-3 mb-6">
        <div class="w-full px-3 mb-6 md:mb-0">
            <label
            class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
            for="nameField"
            >
            Your Name
            </label>
            <input
            class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white"
            id="nameField"
            type="text"
            placeholder="Your name"
            />
            <p class="text-red-500 text-xs italic">Please fill out this field.</p>
        </div>
        <div class="w-full px-3">
            <label
            class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
            for="contactField"
            >
            Your Contact
            </label>
            <input
            class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
            id="contactField"
            type="text"
            placeholder="Enter here"
            />
        </div>
        <div class="w-full px-3">
            <label
            class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
            for="addressField"
            >
            Address
            </label>
            <textarea
            class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
            id="addressField"
            type="text"
            placeholder="Enter here"
            ></textarea>
        </div>
        <p class="ml-4">Important Links</p>
        <div class=" flex-wrap flex-1 w-64  mb-6">
        <div class="w-full px-3 mb-6 md:mb-0">
            <label
            class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
            for="fbField"
            >
            Facebook
            </label>
            <input
            class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white"
            id="fbField"
            type="text"
            placeholder="facebook"
            />
            <p class="text-red-500 text-xs italic">Please fill out this field.</p>
        </div>
            <div class="w-full px-3">
            <label
                class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
                for="instaField"
            >
                Instagram
            </label>
            <input
                class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                id="instaField"
                type="text"
                placeholder="Enter here"
            />
            </div>
            <div class="w-full px-3">
            <label
                class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
                for="linkedField"
            >
                LinkedIn
            </label>
            <input
                class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                id="linkedField"
                type="text"
                placeholder="Enter here"
            />
            </div>
        </div>
        </div>
        <div class="flex-1 w-w-96 ">
            <h3>Professional Information</h3>
            <div class="w-full px-3">
            <label
            class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
            for=""
            >
            Objective
            </label>
            <textarea
            class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
            placeholder="Enter here"
            ></textarea>
        </div>
        <div class="w-full px-3">
            <label
            class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
            for=""
            >
            work Experiance
            </label>
            <textarea
            class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
            placeholder="Enter here"
            ></textarea>
            <div class="container text-center mt-2">
                <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Add</button>
            </div>
        </div>
        </div>
        </div>
    </form>
    </template>