# 接入系统管理类API
### 删除用户组成员

-------

#### URL

> DELETE /api/c/compapi/v2/iam/management/groups/{group_id}/members/
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
| type | string | 是 | query | 成员类型，user表示用户，department表示部门 |
| ids |  string  | 是   | query | 成员ID列表，多个以英文逗号分隔, 对于type=user，则ID为用户名，对于type=department，则为部门ID |

#### Request
```
Delete /api/c/compapi/v2/iam/management/groups/1/members/?type=user&ids=admin,test1,test2
```

#### Response

> Status: 200 OK

```json
{
  "code": 0,
  "message": "ok",
  "data": {}
}
```
