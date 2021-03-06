## 功能描述
Put Bucket Policy请求可以向Bucket写入权限策略，当Bucket已存在权限策略时，该请求上传的策略将覆盖原有的权限策略。支持通配符*
只有Bucket所有者有权限发起该请求，假如您拥有Put Bucket Policy的权限时，将返回405 Method Not Allowed，其余情况返回403 Access Denied

## 请求

### 请求语法

```http
PUT /?policy Http/1.1
Host:<Bucketname>-<UID>.<Region>.myqcloud.com
Date: date
Content-Type:application/json
Content-MD5:MD5
Authorization: Auth String
```

### 请求参数

无特殊请求参数

### 请求头部

无特殊请求头部，其他头部请参见公共请求头部

### 请求内容

```json
{	
    "version":"2.0",
    "principal":   {"qcs":["qcs::cam::uin/<RootAccout>:uin/<SubAccount>","qcs::cam::uin/<RootAccout>:uin/<SubAccount>"]},
    "statement":
    [
       {
            "effect":"allow",        
            "action":["name/cos:<ActionName>"],
            "resource":["qcs::cos:<Region>:uid/<Accout>:prefix//<uid>/<BucketName>/<ObjectName>",
                      "qcs::cos:<Region>:uid/<Accout>:prefix//<uid>/<BucketName>/[dir1]/*"],
        }
        {
            "effect":"allow",        
            "action":["name/cos:<ActionName>"],
            "resource":["qcs::cos:<Region>:uid/<Accout>:prefix//<uid>/<BucketName>/<ObjectName>",
                      "qcs::cos:<Region>:uid/<Accout>:prefix//<uid>/<BucketName>/[dir1]/*"],
        }
    ]
}
```

## 返回值

### 返回头部

无特殊返回头部，其他头部请参见公共返回头部

### 返回内容

无返回内容