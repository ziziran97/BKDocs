# 接入系统管理类API
### 创建用户组

-------

#### URL

> POST /api/c/compapi/v2/iam/management/grade_managers/{grade_manager_id}/groups/
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
| grade_manager_id | int | 是 | path | 分级管理员ID |
| groups |  array[object]  | 是 | body | 用户组列表 |

groups
| 字段 |  类型 |是否必须  | 位置 |描述  |
|--------|--------|--------|--------|--------|
| name |  string  | 是   | body |用户组名称，至少5个字符，同一个分级管理员下唯一 |
| description | string | 是 | body | 用户组描述，至少10个字符 |
| readonly | bool | 否 | body |可选参数，默认为false, 用户组仅仅可读，true时，则无法用户组在权限中心产品上将无法删除 |

#### Request
```json
{
  "groups": [
    {
      "name": "test1",
      "description": "test1test1"
    },
    {
      "name": "test2",
      "description": "test1test2",
      "readonly": true
    },
  ]
}
```

#### Response

| 字段      | 类型      | 描述      |
|-----------|-----------|-----------|
| data |  array[int]  | 用户组ID列表 |

> Status: 200 OK

```json
{
  "code": 0,
  "message": "ok",
  "data": [1, 2]
}
```
