# 接入系统管理类API
### 查询用户组成员列表

-------

#### URL

> GET /api/c/compapi/v2/iam/management/groups/{group_id}/members/
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
| group_id | int | 是 | path | 用户组ID |
| limit |  int  | 是| query | 分页查询参数之一，limit表示查询数量，`最大值为100` |
| offset  | int | 是| query | 分页查询参数之一，offset表示从第几个开始查询，offset从0开始计算 |

#### Request
```
Get /api/c/compapi/v2/iam/management/groups/1/members/?offset=0&limit=10
```

#### Response

| 字段      | 类型      | 描述      |
|-----------|-----------|-----------|
| count   | int     |  总数量 |
| results   |  array[object]   |  分页查询到结果 |

results
| 字段      | 类型      | 描述      |
|-----------|-----------|-----------|
| type | string | 成员类型，user表示用户，department表示部门
| id   | string     | 用户或部门ID |
| name | string | 用户或部门名称 |
| expired_at | int | 过期时间戳(单位秒)，即用户或部门在expired_at后将不具有该用户组的相关权限，其中值为4102444800表示永久 |

> Status: 200 OK

```json
{
  "code": 0,
  "message": "ok",
  "data": {
    "count": 2,
    "results": [
      {
        "type": "user",
        "id": "admin",
        "name": "管理员",
        "expired_at": 1619587562
      },
      {
        "type": "department",
        "id": "1",
        "name": "部门1",
        "expired_at": 4102444800
      }
    ]
  }
}
```
