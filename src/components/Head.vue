<template>
  <b-row>
    <b-col cols="6">
      <b-input placeholder="Input href" v-model="src"></b-input>
    </b-col>
    <b-col cols="2">
      <b-btn @click="loadUrl">Load Remote</b-btn>
    </b-col>
    <b-col cols="2">
      <b-btn @click="clickLoad">Load Local</b-btn>
      <input type="file" id="files" ref="refFile" style="display: none" @change="fileLoad">
    </b-col>
  </b-row>
</template>

<script>
function IsURL(str_url) {
  var strRegex = '^((https|http|ftp|rtsp|mms)?://)'
      + '?(([0-9a-z_!~*\'().&=+$%-]+: )?[0-9a-z_!~*\'().&=+$%-]+@)?' //ftp的user@
      + '(([0-9]{1,3}.){3}[0-9]{1,3}' // IP形式的URL- 199.194.52.184
      + '|' // 允许IP和DOMAIN（域名）
      + '([0-9a-z_!~*\'()-]+.)*' // 域名- www.
      + '([0-9a-z][0-9a-z-]{0,61})?[0-9a-z].' // 二级域名
      + '[a-z]{2,6})' // first level domain- .com or .museum
      + '(:[0-9]{1,4})?' // 端口- :80
      + '((/?)|' // a slash isn't required if there is no file name
      + '(/[0-9a-z_!~*\'().;?:@&=+$,%#-]+)+/?)$';
  var re = new RegExp(strRegex);
  //re.test()
  if (re.test(str_url)) {
    return true;
  } else {
    return false;
  }
}

export default {
  name: 'Head',
  data() {
    return {
      src: '',
    }
  },
  methods: {
    loadUrl() {
      console.log(IsURL(this.src))
    },
    clickLoad() {
      // 下面三种方法实现效果一样
      //方法一: 原生html
      // document.getElementById('files').click();
      // 方法二: jquery实现
      // $("#files").click();
      //方法三:Vue实现
      this.$refs.refFile.dispatchEvent(new MouseEvent('click'))
    },
    fileLoad() {
      //获取读取的文件File对象 下面两种方法实现效果一样
      //方法一:原生html获取
      // const selectedFile = document.getElementById('files').files[0];
      //方法二:Vue实现
      const selectedFile = document.getElementById("files").files[0];
      var fileURL = URL.createObjectURL(selectedFile)
      console.log(fileURL);
      document.getElementById('player').src  = fileURL
      // document.getElementById("player").src = fileURL
      var name = selectedFile.name; //选中文件的文件名
      var size = selectedFile.size; //选中文件的大小
      console.log("文件名:" + name + "大小:" + size);

    }
  }
}
</script>

