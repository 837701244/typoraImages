## 0.安装element

```javascript
vue add element
```

选择如下安装选项:

![image-20220223102021890](https://woniumd.oss-cn-hangzhou.aliyuncs.com/java/cuijin/20220223102031.png)



## 1.Layout 布局

通过基础的 24 分栏，迅速简便地创建布局。

通过 row 和 col 组件，并通过 col 组件的 span 属性我们就可以自由地组合布局。

```html

<el-row>
  <el-col :span="24"><div class="grid-content bg-purple-dark"></div></el-col>
</el-row>

<el-row>
  <el-col :span="12"><div class="grid-content bg-purple"></div></el-col>
  <el-col :span="12"><div class="grid-content bg-purple-light"></div></el-col>
</el-row>
 <el-row >
          <el-col :span="24" class="border">111</el-col>
          <el-col :span="12" class="border">222</el-col>
          <el-col :span="12" class="border">333</el-col>
          <el-col :span="6" class="border">333</el-col>
          <el-col :span="6" class="border">333</el-col>
          <el-col :span="6" class="border">333</el-col>
          <el-col :span="6" class="border">333</el-col>
          <el-col :span="4" class="border">333</el-col>
          <el-col :span="4" class="border">333</el-col>
          <el-col :span="4" class="border">333</el-col>
          <el-col :span="4" class="border">333</el-col>
          <el-col :span="4" class="border">333</el-col>
          <el-col :span="4" class="border">333</el-col>
      </el-row>
```



![image-20220223120512600](https://woniumd.oss-cn-hangzhou.aliyuncs.com/java/cuijin/20220223120515.png)

## 后台布局

## Container 布局容器

用于布局的容器组件，方便快速搭建页面的基本结构：

`<el-container>`：外层容器。当子元素中包含 `<el-header>` 或 `<el-footer>` 时，全部子元素会垂直上下排列，否则会水平左右排列。

`<el-header>`：顶栏容器。

`<el-aside>`：侧边栏容器。

`<el-main>`：主要区域容器。

`<el-footer>`：底栏容器。

```js
<template>
    <el-container>
        <el-aside width="200px" class="bg-dark bg-inverse h-100 sk_side">
            <ul class="padding margin height-big">
                <li>
                    <router-link to="/admin">后台首页</router-link>
                </li>
                <li>
                    <router-link to="/admin/usermanage">用户管理</router-link>
                </li>
                <li>
                    <router-link to="/">前台首页</router-link>
                </li>
            </ul>
        </el-aside>
        <el-main>
            <router-view>管理二级栏目出口</router-view>
        </el-main>
    </el-container>

</template>
```





## 2. 按钮

```javascript
<el-row>
  <el-button>默认按钮</el-button>
  <el-button type="primary">主要按钮</el-button>
  <el-button type="success">成功按钮</el-button>
  <el-button type="info">信息按钮</el-button>
  <el-button type="warning">警告按钮</el-button>
  <el-button type="danger">危险按钮</el-button>
</el-row>

<el-row>
  <el-button plain>朴素按钮</el-button>
  <el-button type="primary" plain>主要按钮</el-button>
  <el-button type="success" plain>成功按钮</el-button>
  <el-button type="info" plain>信息按钮</el-button>
  <el-button type="warning" plain>警告按钮</el-button>
  <el-button type="danger" plain>危险按钮</el-button>
</el-row>

<el-row>
  <el-button round>圆角按钮</el-button>
  <el-button type="primary" round>主要按钮</el-button>
  <el-button type="success" round>成功按钮</el-button>
  <el-button type="info" round>信息按钮</el-button>
  <el-button type="warning" round>警告按钮</el-button>
  <el-button type="danger" round>危险按钮</el-button>
</el-row>

<el-row>
  <el-button icon="el-icon-search" circle></el-button>
  <el-button type="primary" icon="el-icon-edit" circle></el-button>
  <el-button type="success" icon="el-icon-check" circle></el-button>
  <el-button type="info" icon="el-icon-message" circle></el-button>
  <el-button type="warning" icon="el-icon-star-off" circle></el-button>
  <el-button type="danger" icon="el-icon-delete" circle></el-button>
</el-row>


<el-row>
  <el-button icon="el-icon-search" circle></el-button>
  <el-button type="primary" icon="el-icon-edit" circle></el-button>
  <el-button type="success" icon="el-icon-check" circle></el-button>
  <el-button type="info" icon="el-icon-message" circle></el-button>
  <el-button type="warning" icon="el-icon-star-off" circle></el-button>
  <el-button type="danger" icon="el-icon-delete" circle></el-button>
</el-row>

加载中
点击按钮后进行数据加载操作，在按钮上显示加载状态。
<el-button type="primary" :loading="true">加载中</el-button>
```

![image-20220223120445380](https://woniumd.oss-cn-hangzhou.aliyuncs.com/java/cuijin/20220223120447.png)

## 3.表单

```javascript
 <el-form label-width="80px" style="width:400px;margin:0px auto;padding-bottom: 50px">

                    <el-form-item label="用户名:">
                        <el-input placeholder="请输入用户名:" prefix-icon="el-icon-s-custom" clearable v-model.trim="user.userName" style="width:300px"></el-input>
                    </el-form-item>

                    <el-form-item label="密码:">
                        <el-input placeholder="请输入密码:" prefix-icon="el-icon-lock" clearable show-password v-model.trim="user.userPass" style="width:300px"></el-input>
                    </el-form-item>

                    <el-form-item label="手机号:">
                        <el-input placeholder="请输入手机号:"  prefix-icon="el-icon-phone" clearable  v-model.trim="user.userPhone" style="width:300px"></el-input>
                    </el-form-item>

                    <el-form-item label="邮箱:">
                        <el-input placeholder="请输入邮箱"  prefix-icon="el-icon-message" clearable v-model.trim="user.email"  style="width:300px"></el-input>
                    </el-form-item>

                    <el-form-item label="性别:">
                        <el-radio v-model="user.sex" label="男" ></el-radio>
                        <el-radio v-model="user.sex" label="女"></el-radio>
                    </el-form-item>
                    <el-form-item label="爱好:">
                        <el-checkbox v-model="user.hobby" label="篮球"></el-checkbox>
                        <el-checkbox v-model="user.hobby" label="足球"></el-checkbox>
                        <el-checkbox v-model="user.hobby" label="羽毛球"></el-checkbox>
                        <el-checkbox v-model="user.hobby" label="乒乓球"></el-checkbox>
                        <el-checkbox v-model="user.hobby" label="web" disabled></el-checkbox>
                    </el-form-item>
                    <el-form-item label="城市">
                        <el-select v-model="user.city" style="width: 300px">
                            <el-option label="北京" value="北京"></el-option>
                            <el-option label="上海" value="上海"></el-option>
                            <el-option label="广州" value="广州"></el-option>
                            <el-option label="深圳" value="深圳"></el-option>
                        </el-select>
                    </el-form-item>
                    <el-row>
                        <el-col :span="24" style="text-align: center">
                            <el-button type="primary" @click="getFormData">提交</el-button>
                            <el-button type="warning" @click="clearFormData">重置</el-button>
                        </el-col>
                    </el-row>
                </el-form>
```

![image-20220223144916274](https://woniumd.oss-cn-hangzhou.aliyuncs.com/java/cuijin/20220223144918.png)

## 4. 弹框

```javascript
 <el-button type="primary" @click="dialogFormVisible = true">添加用户</el-button>
      <el-dialog title="添加用户" :visible.sync="dialogFormVisible">
          //放置form表单
          <div slot="footer" class="dialog-footer">
              <el-button @click="dialogFormVisible = false">取 消</el-button>
              <el-button type="primary" >确 定</el-button>
          </div>
     </el-dialog>
```

## 5. 消息框

```javascript
<1>.组件中使用this.$message({}) 调用消息框
拥有2个参数:
message:提示的消息
type:消息类型(success,error,warning);
<2>.this.$notify({
                });
title: 消息框的标题
message: 消息框的内容
type: 消息类型(success,error,warning);
<3>.  this.$confirm('此操作将永久删除该文件, 是否继续?', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          type: 'warning'
        })            
```

## 6. 表格

```javascript
<el-table :data="userList" border @selection-change="checkboxSelect">
                  <el-table-column type="selection"   label="选项" align="center" prop="id">
                  </el-table-column>
                  <el-table-column prop="id" label="编号" align="center"></el-table-column>
                  <el-table-column prop="userName" label="用户名" align="center"></el-table-column>
                  <el-table-column prop="userPass" label="密码" align="center"></el-table-column>
                  <el-table-column prop="userPhone" label="手机号" align="center"></el-table-column>
                  <el-table-column prop="userType"  label="用户类型" align="center">
                      <template slot-scope="scope">{{scope.row.userType}}</template>
                  </el-table-column>
                  <el-table-column  label="操作" align="center">
                      <template slot-scope="scope">
                          <el-button type="info" plain size="min" @click="showUser(scope.row)">修改</el-button>
                          <el-button type="danger" plain size="min" @click="deleteUser(scope.row.id)">删除</el-button>
                      </template>
                  </el-table-column>
              </el-table>
```

## 7.分页

```javascript
<el-pagination
                      @size-change="handleSizeChange"
                      @current-change="handleCurrentChange"
                      :current-page="pageData.currentPage"
                      :page-sizes="[5, 10, 15, 20]"
                      :page-size="pageData.pageSize"
                      :total="total"
                      layout="total, sizes, prev, pager, next, jumper"
                      style="text-align: center"
              ></el-pagination>
```



## 8.文件上传

```javascript
<el-upload
        action="#"
        list-type="picture-card"
        :auto-upload="false"
        :on-success="handlerSuccess"
        name="filmImg"
        ref="upload"
        :on-change="change01"
       >
    <i slot="default" class="el-icon-plus"></i>
</el-upload>
```



## 9.官网

```javascript
小图标:https://element.eleme.cn/2.13/#/zh-CN/component/icon
常用组件:https://element.eleme.cn/2.13/#/zh-CN/component
```

## 在页面中解决css冲突

```js
<style scoped>
    /deep/
</style
不支持scss语言
在最前面需要加/deep/
```

