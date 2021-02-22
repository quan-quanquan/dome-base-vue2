<template>
  <div>
    <el-upload
      action="#"
      :before-upload="handleFile"
    >
      <el-button size="small" type="primary">点击上传</el-button>
    </el-upload>
  </div>
</template>
<script>
export default {
  props: {
    sliceSize: {
      type: Number,
      default: () => 1000
    },
    concurrence: {
      type: Number,
      default: () => 3
    }
  },
  methods: {
    handleFile(file) {
      console.log(file)
      this.generateSlice(file)
    },
    generateSlice(file) {
      let sliceList = []
      let cur = 0
      let names = file.name.split('.')
      let fileName = names.splice(0, names.length - 1).join()
      let extension = names.pop()
      while(cur < file.size) {
        let slice = {
          chunk: file.slice(cur, cur + this.sliceSize),
          name: fileName + '~' + sliceList.length + '.' + extension,
          type: file.type
        }
        console.log(slice)
        sliceList.push(slice)
        cur += this.sliceSize
      }
    }
  }
}
</script>