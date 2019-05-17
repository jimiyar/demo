<template>
	<div>
        <el-form ref="form" :model="form" :rules="rules" label-width="80px">
            <el-form-item label="姓名" prop="named">
                <el-input v-model="form.named" ></el-input>
            </el-form-item>
            <el-form-item label="性别" prop="sex">
                <el-select v-model="form.sex" placeholder="请选择" >
                    <el-option label="男" value="man"></el-option>
                    <el-option label="女" value="woman"></el-option>
                </el-select>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="onSubmite('form')">确定</el-button>
                <el-button type="primary" @click="resetForm('form')">重置</el-button>
            </el-form-item>
        </el-form>   
    </div>
</template>

<script>
export default {
  name:HelloWorld,
  components:{
    HelloWorld
  },
  data () {
    return{
  form:{
          named:"",
          sex:""
        },
        rules:{
          named :[{required: true, message: '请输入', trigger: 'blur'}],
          sex :[{required: true, message: '请输入', trigger: 'blur'}]
        }
    }
  },
    methods: {
        onSubmite(formData) {
            this.$refs[formData].validate((valid) => {
                if (!valid) {         
                    console.log(this.form) 
                }
            });
        },
        resetForm(formData) {
            this.$refs[formData].resetFields();//表单重置
        }
    }	
}
</script>
<style scoped>
</style>
