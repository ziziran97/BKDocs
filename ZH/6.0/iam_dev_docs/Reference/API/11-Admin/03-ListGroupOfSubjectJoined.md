# 超级管理类API
### 查询Subject加入的用户组列表

-------

#### URL

> GET /api/c/compapi/v2/iam/admin/subjects/{subject_type}/{subject_id}/groups/
> `特别说明:该 API 为ESB API` [ESB API 说明](../01-Overview/01-BackendAPIvsESBAPI.md)


#### Parameters

* 通用参数

| 字段 |  类型 |是否必须  | 描述  |
|--------|--------|--------|--------|
|bk_app_code|string|是|应用 ID|
|bk_app_secret|string|是|安全密钥(应用 TOKEN)，可以通过 蓝鲸智云开发者中心 -> 点击应用 ID -> 基本信息 获取|
|bk_token|string|否|当前用户登录态，bk_token 与 bk_username 必须一个有效，bk_token 可以通过 Cookie 获取|
|bk_username|string|否|当前用户用户名，仅仅在 ESB 里配置免登录态验证白名单中的应用，才可以用此字段指定当前用户|

* 接口参数

| 字段 |  类型 |是否必须  | 位置 |描述  |
|--------|--------|--------|--------|--------|
| subject_type | string | 是 | path | Subject类型，user表示用户，department表示部门 |
| subject_id | string | 是 | path | 部门ID或用户名 | 

#### Request
```
Get /api/c/compapi/v2/iam/admin/subjects/user/admin/groups/
```

#### Response

| 字段      | 类型      | 描述      |
|-----------|-----------|-----------|
| id   | int     | 用户组ID |
| name | string | 用户组名称 |
| expired_at | int | 过期时间戳(单位秒)，即用户或部门在expired_at后将不具有该用户组的相关权限，其中值为4102444800表示永久 |


> Status: 200 OK

```json
{
  "code": 0,
  "message": "ok",
  "data": [
     {
       "id": 1,
       "name": "test1",
       "expired_at": 1619587562
     },
     {
       "id": 2,
       "name": "test2",
       "expired_at": 1619587562
     },
     {
       "id": 2,
       "name": "test2",
       "expired_at": 1619587562
     }
  ]
}
```
