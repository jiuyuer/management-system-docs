```javascript
const express = require('express');
const env = process.env.NODE_ENV || 'development';
const app = express();

app.use(express.static('./dist'));

const server = app.listen(4000, () => {
  console.log(
    `Express started in ${app.get('env')} mode on http://localhsot:4000`
  );
});
```

```nginx
upstream xxxuthus {
  server 127.0.0.1:4000;
}

server {
  listen 80;
  server_name www.xxxuthus.cn;

  location / {
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forward-For $proxy_add_x_forwarded_for;
    proxy_set_header Host $http_host;
    proxy_set_header X-Nginx-Proxt true;

    proxy_pass http://xxxuthus;
    proxy_redirect off;
  }

  location ~* ^.+\.(jpg|jpeg|gif|png|ico|css|js|pdf|txt) {
    root /www/vnpastime/production/current/dist;
  }
}
```

```vue
<el-form :inline="true" ref="form" :model="form" size="mini" label-width="80px">
  <el-form-item label="活动名称">
    <el-input v-model="form.name"></el-input>
  </el-form-item>
  <el-form-item label="活动区域">
    <el-select v-model="form.region" placeholder="请选择活动区域">
      <el-option label="区域一" value="shanghai"></el-option>
      <el-option label="区域二" value="beijing"></el-option>
    </el-select>
  </el-form-item>
  <el-form-item label="活动时间">
    <el-date-picker v-model="form.date" type="daterange" range-separator="至" start-placeholder="开始日期" end-placeholder="结束日期">
    </el-date-picker>
  </el-form-item>
  <el-form-item label="">
    <el-button type="primary" icon="el-icon-search">搜索</el-button>
    <el-button>重置</el-button>
  </el-form-item>
</el-form>
```

```css
.line {
  text-align: center;
}
```
