<!-- <template>
<div class="flex flex-col">
  <div class="overflow-x-auto sm:-mx-6 lg:-mx-8">
    <div class="py-2 inline-block min-w-full sm:px-6 lg:px-8">
      <div class="overflow-x-auto">
        <form>
        <table class="min-w-50">
          <thead class="border-b">
            
            <tr>
              <th scope="col" class="text-sm font-medium text-gray-900 px-4 py-2 text-left">
                #
              </th>
              <th scope="col"  class="text-sm font-medium text-gray-900 px-4 py-2 text-left">
               Player 
              </th>
              <th scope="col" class="text-sm font-medium text-gray-900 px-4 py-2 text-left"  >
              Team
              </th>
              <th scope="col" class="text-sm font-medium text-gray-900 px-4 py-2 text-left">
                Number
              </th>
              <th scope="col" class="text-sm font-medium text-gray-900 px-4 py-2 text-left">
                Position
              </th>
              <th scope="col" class="text-sm font-medium text-gray-900 px-4 py-2 text-left">
                LAST ATTENDED
              </th>
              <th scope="col" class="text-sm font-medium text-gray-900 px-6 py-4 text-left">
                Country
              </th>
               <th scope="col" class="text-sm font-medium text-gray-900 px-6 py-4 text-left">
                <button type="button" class="text-sm text-gray-900 font-bold px-4 py-2 whitespace-nowrap">ADD</button>
              </th>
            </tr>
          </thead>
          <tbody>
            <tr class="border-b" v-for="(item,index) in users" v-bind:index="index" :key="index">
              <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">1</td>
              <td class="text-sm text-gray-900 font-light px-4 py-2 whitespace-nowrap">
                Stephen Curry
              </td>
              <td class="text-sm text-gray-900 font-light px-4 py-2 whitespace-nowrap">
                GSW
              </td>
              <td class="text-sm text-gray-900 font-light px-4 py-2 whitespace-nowrap">
                30
              </td>
              <td class="text-sm text-gray-900 font-light px-4 py-2 whitespace-nowrap">
               G 
              </td>
              <td class="text-sm text-gray-900 font-light px-4 py-2 whitespace-nowrap">
                Davidson
              </td>
              <td class="text-sm text-gray-900 font-light px-4 py-2 whitespace-nowrap">
                USA
              </td>
              <td>
              <button  type="button" class="text-sm text-gray-900 font-bold px-4 py-2 whitespace-nowrap" @click="onEdit(index)">Edit</button>
             </td>
             <td>
              <button  type="button" class="text-sm text-gray-900 font-bold px-4 py-2 whitespace-nowrap" @click="userDelete(index)">Delete</button>
             </td>
            
            </tr>
            <tr class="bg-white border-b">
              <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">2</td>
              <td class="text-sm text-gray-900 font-light px-4 py-2 whitespace-nowrap">
              ROhit Sharma
              </td>
              <td class="text-sm text-gray-900 font-light px-4 py-2 whitespace-nowrap">
                MI
              </td>
              <td class="text-sm text-gray-900 font-light px-4 py-2 whitespace-nowrap">
                20
              </td>
              <td class="text-sm text-gray-900 font-light px-4 py-2 whitespace-nowrap">
                G
              </td>
              <td class="text-sm text-gray-900 font-light px-4 py-2 whitespace-nowrap">
                MI
              </td>
              <td class="text-sm text-gray-900 font-light px-4 py-2 whitespace-nowrap">
                India
              </td>
              <td>
              <button  type="button" class="text-sm text-gray-900 font-bold px-4 py-2 whitespace-nowrap" @click="onEdit(index)">Edit</button>
             </td>
             <td>
              <button  type="button" class="text-sm text-gray-900 font-bold px-4 py-2 whitespace-nowrap" @click="userDelete(index)">Delete</button>
             </td>
             
            </tr>
            <tr class="bg-white border-b">
              <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">3</td>
              <td class="text-sm text-gray-900 font-light px-4 py-2 whitespace-nowrap">
                Virat
              </td>
              <td class="text-sm text-gray-900 font-light px-4 py-2 whitespace-nowrap">
                RCB
              </td>
              <td class="text-sm text-gray-900 font-light px-4 py-2 whitespace-nowrap">
                20
              </td>
              <td class="text-sm text-gray-900 font-light px-4 py-2 whitespace-nowrap">
                G
              </td>
              <td class="text-sm text-gray-900 font-light px-4 py-2 whitespace-nowrap">
              Rcb
              </td>
              <td class="text-sm text-gray-900 font-light px-4 py-2 whitespace-nowrap">
                India
              </td>
             <td>
              <button  type="button" class="text-sm text-gray-900 font-bold px-4 py-2 whitespace-nowrap" @click="onEdit(index)">Edit</button>
             </td>
             <td>
              <button  type="button" class="text-sm text-gray-900 font-bold px-4 py-2 whitespace-nowrap" @click="userDelete(index)">Delete</button>
             </td>
            </tr>
          </tbody>
        </table>
        </form>
      </div>
    </div>
  </div>
</div>
<div>
 

 
</div>
</template>


<script>
export default {
    data() {
        return {
            isEdit:false,
            indexEdit:-1,
            users: [],
            user: {
                player: '',
                team: '',
                number: '',
                position: '',
                country: '',
                lastattended:''
            },
        };
    },
    methods: {
        formSubmit(event) {
            event.preventDefault();
            if(this.isEdit==true){
                this.users[this.indexEdit]=this.user;
                this.isEdit=false;
                this.indexEdit=-1;
            }
            else{
                 this.users.push(this.user);
            }
           this.user = {
                  player: '',
                team: '',
                number: '',
                position: '',
                country: '',
                lastattended:''
            };
        },
        // onReset(event) {
        //     event.preventDefault();
        //     this.form.email = "";
        //     this.form.name = "";
        //     this.form.address = "";
        //     this.form.contact = "";
        //     this.form.city=""
        // },
        userDelete(index) {
            this.users.splice(index, 1)
        },
        onEdit(index){
            this.user.player=this.users[index].player;
            this.user.team=this.users[index].team;
            this.user.number=this.users[index].number;
            this.user.position=this.users[index].position;
            this.user.country=this.users[index].country;
            this.user.lastattended=this.users[index].lastattended;
            this.isEdit=true;
            this.indexEdit=index;
        }
    }
}
</script> -->