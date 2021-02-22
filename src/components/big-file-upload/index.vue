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
  data() {
    return {
      sliceList: [],
      uploadUrl: '/'
    }
  },
  methods: {
    requset() {

    },
    handleFile(file) {
      console.log(file)
      this.generateSlice(file)
    },
    generateSlice(file) {
      let sliceList = this.sliceList
      let cur = 0
      let names = file.name.split('.')
      let fileName = names.splice(0, names.length - 1).join()
      let extension = names.pop()
      while(cur < file.size) {
        let slice = {
          chunk: file.slice(cur, cur + this.sliceSize),
          name: fileName + '~' + sliceList.length + '.' + extension,
          type: file.type,
          index: sliceList.length
        }
        console.log(slice)
        sliceList.push(slice)
        cur += this.sliceSize
      }
    },
    uploadSlice() {
      const requestList = this.sliceList.map(slice => {
        const formData = new FormData()
        formData.append('slice', slice)
        return formData
      }).map(data => {
        this.requset(data)
      })

      this.concurrentRequest(requestList)
    },
    concurrentRequest(requestList) {
      let curConcurren = 0
      let datas = []
      let index = 0
      const _request = () => {
        for (let i = index; i < requestList.length && curConcurren < this.concurrence; i++) {
          curConcurren++
          index++
          requestList[i]().then((data) => {
            curConcurren--
            datas.splice(i, 0, data)
            if (index < this.requestList.length) this._request()
          }, (err) => {

          })
        }
      }
      _request()
    }
  }
}
</script>