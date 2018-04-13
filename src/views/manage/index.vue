<template>
  <div class="manage tc">
      <button v-on:click="add">Add</button>
      <div class="input-area" v-show="showAdd">
          <input type="text" placeholder="add admin" v-model="nameValue">
          <button v-on:click="addName">Done</button>
      </div>
      <table>
          <tr>
              <th>name</th>
              <th>operate</th>
          </tr>
          <tr v-for="(item,index) in items">
              <td>
                  {{item.name}}
              </td>
              <td v-bind:id="index">
                  <span v-on:click="edit">editor</span>
                  <span v-on:click="del">delete</span>
              </td>
          </tr>
      </table>
      <!-- editor import -->
      <div class="wrap" v-show="showEdit">
          <div class="content">
              <input type="text" placeholder="new name please" v-model="newName">
              <button v-on:click="cancel">Cancel</button>
              <button v-on:click="done">Done</button>
          </div>
      </div>
      <footer-nav></footer-nav>
  </div>
</template>

<style>
.manage{padding-bottom:50px;}
	.manage >button{width:200px; height:40px; line-height:40px; background-color:#41b883; border: none; border-radius:5px; font-size:16px; color:#fff;}
	table{width:100%; max-width:500px; margin:0 auto; margin-top:0px;}
	.input-area input{width: 200px; height: 30px; line-height:30px; margin:20px 0; outline:none; border:1px solid #333;}
	.input-area button{ width:60px; height: 30px; line-height:30px; background-color:#41b883; border: none; border-radius:5px; font-size:16px; color:#fff;}
	th,td{width:100px;}
	tr input{width:100px; height:30px; padding-left:10px; outline:none; border:1px solid #333;}
	.wrap{display:table; position:fixed; top:0; left:0; height:100%; width:100%; background:rgba(0,0,0,.8); z-index: 10;}
	.wrap .content{display:table-cell; vertical-align:middle;}
	.wrap .content input{height: 40px; line-height: 40px; display:block; margin:0 auto; margin-bottom:10px; font-size:16px;}
	.wrap .content button{width:100px; height: 30px; line-height: 30px; background-color:#41b883; border: none; border-radius:5px; font-size:16px; color:#fff;}
</style>


<script>
import FooterNav from '../../components/footer'
export default {
  components:{
      FooterNav
  },
  data(){
      return{
          isNowPage:true,
          showAdd:false,
          showEdit:false,
          items:[{'name':'Jack'},{'name':'Sam'}],
          nameValue:'',
          newName:'',
          editId:0
      }
  },
  methods:{
      add(){
          this.showAdd=true
      },
      addName(){
          var v=this.nameValue
          if(v.trim()==""){
              alert("name of admin")
          }else{
              var data = {}
              data.name = v
              this.items.push(data)
          }
      },
      del(e){
          var id = e.target.offsetParent.id
          this.items.splice(id,1)
      },
      edit(e){
           var id = e.target.offsetParent.id
           this.showEdit=true
           this.editId=id;
           this.newName=this.items[id].name
      },
      cancel(){
          this.showEdit=false;
      },
      done(){
          var v = this.newName;
          if(v.trim()==""){
              alert("input name");
          }else{
              this.items[this.editId].name=this.newName;
              this.showEdit=false;
          }
      }
  }
}
</script>

