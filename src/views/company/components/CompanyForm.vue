<template>
  <el-form>
    <el-row :gutter="20">
      <el-col :span="8" :xs="24">
        <el-form-item label="Name">
          <el-input v-model.trim="company.username" />
        </el-form-item>
        <el-form-item label="Email Address">
          <el-input v-model.trim="company.email" />
        </el-form-item>
        <el-form-item label="Phone Number">
          <el-input v-model.trim="company.phone" />
        </el-form-item>
      </el-col>
      <el-col :span="8" :xs="24">
        <el-form-item label="Username">
          <el-input v-model.trim="company.username" />
        </el-form-item>
        <el-form-item label="Password">
          <el-input v-model.trim="company.password" />
        </el-form-item>
        <el-form-item label="Password Confirmation">
          <el-input v-model.trim="company.passwordConf" />
        </el-form-item>
      </el-col>
    </el-row>
    <el-row :gutter="20">
      <el-col :span="8" :xs="24">
        <!-- <el-form-item label="Logo">
          <pan-thumb :image="image" @click="imagecropperShow=true"/>
          <el-button type="primary" icon="el-icon-upload" @click="imagecropperShow=true"></el-button>
          <image-cropper
            v-show="imagecropperShow"
            :key="imagecropperKey"
            :width="300"
            :height="300"
            url="https://httpbin.org/post"
            lang-type="en"
            @close="close"
            @crop-upload-success="cropSuccess"
          />
        </el-form-item> -->
        <el-form-item prop="logo" label="Logo">
          <Upload v-model="company.logo" />
        </el-form-item>
      </el-col>
      <el-col :span="8" :xs="24">
        <el-form-item label="Theme">
          <el-col :span="24">
            <el-color-picker v-model="color" size="mini" style="margin-right: 10px"></el-color-picker>
            <el-color-picker v-model="color" size="mini" style="margin-right: 10px"></el-color-picker>
            <el-color-picker v-model="color" size="mini"></el-color-picker>
          </el-col>
        </el-form-item>
      </el-col>
    </el-row>
    <el-form-item>
      <el-button type="primary" @click="create">Create</el-button>
    </el-form-item>
  </el-form>
</template>

<script>
import ImageCropper from '@/components/ImageCropper'
import PanThumb from '@/components/PanThumb'
import Upload from '@/components/Upload/SingleImage2'

export default {
  props: {
    company: {
      type: Object,
      default: () => {
        return {
          name: '',
          email: '',
          phone: '',
          logo: '',
          title: '',
          theme: '',
          username: '',
          password: '',
          passwordConf: '',
        }
      }
    }
  },
  components: { ImageCropper, PanThumb, Upload },
  data() {
    return {
      imagecropperShow: false,
      imagecropperKey: 0,
      image: 'https://wpimg.wallstcn.com/577965b9-bb9e-4e02-9f0c-095b41417191'
    }
  },
  methods: {
    cropSuccess(resData) {
      this.imagecropperShow = false
      this.imagecropperKey = this.imagecropperKey + 1
      this.image = resData.files.avatar
    },
    close() {
      this.imagecropperShow = false
    },
    create() {
      this.$message({
        message: 'Company has been created successfully',
        type: 'success',
        duration: 5 * 1000
      })
    }
  }
}
</script>
