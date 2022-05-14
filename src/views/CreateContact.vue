<template>
    <div>
        <label for="">Contact No</label>
        <input type="text" v-model="contactNo">
          <label for="">Contact Person</label>
        <input type="text" v-model="contactPerson">
          <label for="">Device Code</label>
        <input type="text" v-model="deviceCode">
          <label for="">Relation ship</label>
        <input type="text" v-model="relationship">
        <button v-on:click="CreateContact">建立關係</button>
    </div>
</template>

<script>
    export default{
        data(){
            return{
                contactNo:"",
                contactPerson:"",
                deviceCode:"",
                relationship:"",
            }
        },
        methods:{
            CreateContact(){
                let url="/api/EmergencyContact/create";
                let config={
                    "contactNo": this.contactNo,
                    "contactPerson": this.contactPerson,
                    "deviceCode": this.deviceCode,
                    "relationship": this.relationship

                };
                this.axios.post(url,config)
                .then((res)=>{
                    console.log(res)
                    alert(res.data.contactPerson,"Create Success!")
            })
                .catch((err)=>{console.log(err)})
            },
        }
        ,
        name:"CreateContact"
    }
</script>

<style></style>