
# map-line

获取地图上折线的点位信息


## 安装

git clone https://github.com/zmheang/map-line.git

```bash
  cd map-line
  npm install
  在百度地图上申请ak，填写到app.vue中
  npm run serve
```


## 截图

![App Screenshot](https://gitee.com/koron_1_zmheang0528/imgs/raw/master//imgs/20211019095528.png)


## 用法

- 回退

  清除当前点

- 清空

  清除当前点位列表

- 导出

  导出当前点位信息的json数据

  ```json
  [
    {
      "lat": 38.468342,
      "lng": 105.698767
    },
    {
      "lat": 38.363398,
      "lng": 105.61368
    },
    {
      "lat": 38.231096,
      "lng": 105.726363
    }
  ]
  ```

  
