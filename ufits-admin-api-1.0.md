## 孕产平台后台管理
+ 2019年04月12日
    +  孕产平台后台管理初始化
## 套餐管理
+ Data
  + ProjectCategory - 套餐分类表
    + id (Long) - ID
    + categoryTitle (String) - 分类名称
    + enabled (int) - 0禁用 1启用
    + creator (Long) - 创建人
    + modifier (Long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
  + Project - 套餐(项目)表
    + id (Long) - ID
    + categoryId - 项目分类ID
    + projectTitle (String) - 项目名称
    + classTime (BigDecimal) -课时数/购课数
    + giftClassTime (BigDecimal) - 赠送课时/课数
    + money (BigDecimal) - 金额 
    + unitPrice (BigDecimal) - 单价
    + effectiveDays (int) - 有效时间（单位：天）
    + leaveRestrict (int) - 请假限制，0：不限制，1：不允许，2：有限制
    + leavePermitNum (int) - 请假允许次数
    + leavePermitDays (int) - 请假允许天数
    + leaveMinDays (int) - 一次请假最少天数
    + enabled (int) - 0禁用 1启用
    + creator (Long) - 创建人
    + modifier (Long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间 

### 套餐分类增加[POST] /admin/projectCategories
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
    
      {
         "data":{
    		"categoryTitle":"大班课"
    	  }
      }

+ Response 200 (application/json)

      {
        "data": {
            "id": 6,
            "type": "projectCategories"
        }
      }
### 套餐分类修改 [PUT] /admin/projectCategories/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
    
      {
         "data":{
    		"categoryTitle":"大班课1"
    	  }
      }
+ Response 200 (application/json)

### 套餐分类列表 [GET] /admin/projectCategories
+ Parameters
  + filter[categoryTitle:like]=%25孕%25 （'%25'为'%'的转义）
  + page[number]=1&page[size]=10
  + sort -modified(从新到旧) | modified(从旧到新)
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)

      {
        "meta": {
            "totalPages": 1,
            "totalElements": 4,
            "size": 10,
            "number": 1,
            "numberOfElements": 4,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "/admin/projectCategories?page[number]=1&page[size]=10",
            "first": "/admin/projectCategories?page[number]=1&page[size]=10",
            "last": "/admin/projectCategories?page[number]=1&page[size]=10"
        },
        "data": [
            {
                "id": 1,
                "enabled": 1,
                "creator": 5,
                "modifier": 0,
                "created": "2019-05-06 11:34:40",
                "modified": "2019-05-06 11:34:37",
                "categoryTitle": "免费体验课"
            },
            {
                "id": 2,
                "enabled": 1,
                "creator": 5,
                "modifier": 0,
                "created": "2019-05-06 11:35:07",
                "modified": "2019-05-07 18:07:41",
                "categoryTitle": "收费体验课"
            },
            {
                "id": 3,
                "enabled": 1,
                "creator": 5,
                "modifier": 0,
                "created": "2019-05-06 11:35:44",
                "modified": "2019-05-06 11:35:46",
                "categoryTitle": "孕期瑜伽小班课"
            },
            {
                "id": 4,
                "enabled": 1,
                "creator": 5,
                "modifier": 0,
                "created": "2019-05-06 11:36:11",
                "modified": "2019-05-06 11:36:15",
                "categoryTitle": "孕产套课"
            }
        ]
      }

### 套餐分类删除 [DELETE] /admin/projectCategories/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Response 204


### 套餐增加[POST] /admin/projects
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
    
      {
    	 "data":{
    		"categoryId":2,
    		"projectTitle":"000000节孕产套课",
    		"classTime":"74",
    		"giftClassTime":"2",
    		"money":"6666",
    		"unitPrice":"34",
    		"effectiveDays":"45",
    		"leaveRestrict":"2",
    		"leavePermitNum":"4",
    		"leavePermitDays":"365",
    		"leaveMinDays":"7"
    	 }
      }

+ Response 200 (application/json)

      {
        "data": {
            "id": 22,
            "type": "projects"
        }
      }


### 套餐修改 [PUT] /admin/projects/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
    
      {
    	 "data":{
    		"categoryId":2,
    		"projectTitle":"000000节孕产套课1",
    		"classTime":"74",
    		"giftClassTime":"2",
    		"money":"6666",
    		"unitPrice":"34",
    		"effectiveDays":"45",
    		"leaveRestrict":"2",
    		"leavePermitNum":"4",
    		"leavePermitDays":"365",
    		"leaveMinDays":"7"
    	 }
      }
+ Response 200 (application/json)

### 套餐详情 [GET] /admin/projects/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)

      {
        "data": {
            "id": 9,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-04-15 14:50:32",
            "modified": "2019-04-15 14:50:35",
            "categoryId": 5,
            "projectTitle": "12节孕期瑜伽小班课",
            "classTime": 18,
            "giftClassTime": 0,
            "money": 12000,
            "effectiveDays": 90,
            "leavePermitNum": 3,
            "leavePermitDays": 40,
            "leaveMinDays": 0
        }
      }

### 套餐删除 [DELETE] /admin/projects/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Response 204

### 套餐列表 [GET] /admin/projects
+ Parameters
  + filter[categoryId]=2（套餐分类查询）
  + filter[projectTitle:like]=%25孕%25 （'%25'为'%'的转义）
  + page[number]=1&page[size]=10
  + sort -modified(从新到旧) | modified(从旧到新)
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)

      {
        "meta": {
            "totalPages": 2,
            "totalElements": 16,
            "size": 10,
            "number": 1,
            "numberOfElements": 10,
            "first": true,
            "last": false,
            "sort": null
        },
        "links": {
            "self": "/admin/projects?page[number]=1&page[size]=10",
            "first": "/admin/projects?page[number]=1&page[size]=10",
            "next": "/admin/projects?page[number]=2&page[size]=10",
            "last": "/admin/projects?page[number]=2&page[size]=10"
        },
        "data": [
            {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-15 14:50:11",
                "modified": "2019-04-15 14:50:08",
                "categoryId": 1,
                "projectTitle": "免费体验课",
                "classTime": 0,
                "giftClassTime": 0,
                "money": 0,
                "effectiveDays": 90,
                "leavePermitNum": 0,
                "leavePermitDays": 0,
                "leaveMinDays": 0,
                "categoryTitle": "免费体验课"
            },
            {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-15 14:50:23",
                "modified": "2019-04-15 14:50:19",
                "categoryId": 3,
                "projectTitle": "孕期瑜伽小班课",
                "classTime": 0,
                "giftClassTime": 0,
                "money": 0,
                "effectiveDays": 90,
                "leavePermitNum": 0,
                "leavePermitDays": 0,
                "leaveMinDays": 0,
                "categoryTitle": "孕期瑜伽小班课"
            },
            {
                "id": 4,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-15 14:50:28",
                "modified": "2019-04-15 14:50:26",
                "categoryId": 4,
                "projectTitle": "孕产套课",
                "classTime": 0,
                "giftClassTime": 0,
                "money": 0,
                "effectiveDays": 90,
                "leavePermitNum": 0,
                "leavePermitDays": 0,
                "leaveMinDays": 0,
                "categoryTitle": "孕产套课"
            },
            {
                "id": 9,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-15 14:50:32",
                "modified": "2019-04-15 14:50:35",
                "categoryId": 5,
                "projectTitle": "12节孕期瑜伽小班课",
                "classTime": 18,
                "giftClassTime": 0,
                "money": 12000,
                "effectiveDays": 90,
                "leavePermitNum": 3,
                "leavePermitDays": 40,
                "leaveMinDays": 0,
                "categoryTitle": "测试"
            },
            {
                "id": 15,
                "enabled": 1,
                "creator": 5,
                "modifier": 0,
                "created": "2019-05-06 11:41:33",
                "modified": "2019-05-06 11:41:36",
                "categoryId": 3,
                "projectTitle": "孕期瑜伽小班课子项1",
                "classTime": 10,
                "giftClassTime": 2,
                "money": 1500,
                "unitPrice": 200,
                "effectiveDays": 30,
                "leaveRestrict": 2,
                "leavePermitNum": 5,
                "leavePermitDays": 2,
                "leaveMinDays": 1,
                "categoryTitle": "孕期瑜伽小班课"
            },
            {
                "id": 16,
                "enabled": 1,
                "creator": 5,
                "modifier": 0,
                "created": "2019-05-06 11:44:03",
                "modified": "2019-05-06 11:44:05",
                "categoryId": 4,
                "projectTitle": "孕产套课子项1",
                "classTime": 40,
                "giftClassTime": 5,
                "money": 6000,
                "unitPrice": 300,
                "effectiveDays": 60,
                "leaveRestrict": 0,
                "leavePermitNum": 10,
                "leavePermitDays": 5,
                "leaveMinDays": 1,
                "categoryTitle": "孕产套课"
            }
        ]
      }

## 课程管理
+ 课程分类
+ Data
  + AttendClassCategory - 课程分类表
    + id (Long) - ID
    + categoryTitle (String) - 分类名称
    + description (String) - 分类描述
    + nature (int) - 课程性质，0：公开，1：私教
    + enabled (int) - 0禁用 1启用
    + creator (Long) - 创建人
    + modifier (Long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间

### 课程分类增加[POST] /admin/attendClassCategories
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
    
      {
         "data":{
		     "categoryTitle":"查房000",
		     "description":"查房描述000！",
		     "nature":1
	    }
      }

+ Response 200 (application/json)

      {
        "data": {
            "id": 6,
            "type": "attendClassCategories"
        }
      }
### 课程分类修改 [PUT] /attendClassCategories/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Request (application/json)
    
      {
    	"data":{
    		"categoryTitle":"查房0001",
    		"description":"查房描述0001",
    		"nature":1
    	 }
      }
+ Response 200 (application/json)

### 课程分类详情 [GET] /attendClassCategories/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Response 200 (application/json)

      {
        "data": {
            "id": 6,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-05-08 10:19:05",
            "modified": "2019-05-08 10:20:38",
            "categoryTitle": "查房0001",
            "description": "查房描述0001",
            "nature": 1
        }
      }

### 课程分类列表 [GET] /admin/attendClassCategories
+ Parameters
  + filter[categoryTitle:like]=%25查%25 （'%25'为'%'的转义）
  + page[number]=1&page[size]=10
  + sort -modified(从新到旧) | modified(从旧到新)
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)

      {
        "meta": {
            "totalPages": 1,
            "totalElements": 6,
            "size": 10,
            "number": 1,
            "numberOfElements": 6,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "/admin/attendClassCategories?page[number]=1&page[size]=10",
            "first": "/admin/attendClassCategories?page[number]=1&page[size]=10",
            "last": "/admin/attendClassCategories?page[number]=1&page[size]=10"
        },
        "data": [
            {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-05-05 14:35:37",
                "modified": "2019-05-05 14:35:31",
                "categoryTitle": "公开课",
                "nature": 0
            },
            {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-05-05 14:35:40",
                "modified": "2019-05-05 14:35:34",
                "categoryTitle": "私教课",
                "nature": 1
            },
            {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-05-05 14:29:28",
                "modified": "2019-05-05 14:29:28",
                "categoryTitle": "助教",
                "description": "描述内容！！！",
                "nature": 0
            },
            {
                "id": 4,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-05-05 14:30:07",
                "modified": "2019-05-05 14:30:07",
                "categoryTitle": "小班课",
                "description": "描述信息！！",
                "nature": 1
            },
            {
                "id": 6,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-05-08 10:19:05",
                "modified": "2019-05-08 10:20:38",
                "categoryTitle": "查房0001",
                "description": "查房描述0001",
                "nature": 1
            }
        ]
      }

### 课程分类删除 [DELETE] /admin/attendClassCategories/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Response 204

+ 课程服务
+ Data
  + CourseLevel - 课程分类（级别）表 
    + levelTitle (String) - 级别名称
    + description (String) - 级别描述
    + timeCoefficient (BigDecimal) - 时长系数
    + enabled (int) - 0禁用 1启用
    + creator (Long) - 创建人
    + modifier (Long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
  + Course - 课程表
    + levelId (Long) - 级别标识
    + courseTitle (String) - 课程名称
    + thumbnail (String) - 缩略图
    + description (String) - 课程描述
    + content (String) - 课程内容
    + recommend (int) - 是否推荐（默认0：不推荐，1：推荐）
    + enabled (int) - 0禁用 1启用
    + creator (Long) - 创建人
    + modifier (Long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
    + pictures - 图片

### 课程服务增加[POST] /admin/courseLevels
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
    
      {
    	 "data":{
    		 "levelTitle":"中高级00",
    		 "description":"级别描述信息00",
    	 	 "timeCoefficient":"1.70"
    	 }
      }

+ Response 200 (application/json)

      {
        "data": {
            "id": 5,
            "type": "courseLevels"
        }
      }
### 课程服务修改 [PUT] /admin/courseLevels/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
    
      {
    	 "data":{
    		 "levelTitle":"中高级123",
    		 "description":"级别描述信息123",
    		 "timeCoefficient":"1.70"
    	 }
      }
+ Response 200 (application/json)

### 课程服务列表 [GET] /admin/courseLevels
+ Parameters
  + filter[levelTitle:like]=%25高孕%25 （'%25'为'%'的转义）
  + page[number]=1&page[size]=10
  + sort -modified(从新到旧) | modified(从旧到新)
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)
    
      {
        "meta": {
            "totalPages": 1,
            "totalElements": 6,
            "size": 10,
            "number": 1,
            "numberOfElements": 6,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "/admin/courseLevels?page[number]=1&page[size]=10",
            "first": "/admin/courseLevels?page[number]=1&page[size]=10",
            "last": "/admin/courseLevels?page[number]=1&page[size]=10"
        },
        "data": [
            {
                "id": 1,
                "created": "2019-04-10 15:19:18",
                "modified": "2019-04-10 15:19:18",
                "levelTitle": "初级"
            },
            {
                "id": 2,
                "created": "2019-04-10 18:34:48",
                "modified": "2019-04-10 18:34:43",
                "levelTitle": "中级"
            },
            {
                "id": 3,
                "created": "2019-04-10 18:34:51",
                "modified": "2019-04-10 18:34:46",
                "levelTitle": "高级"
            },
            {
                "id": 4,
                "created": "2019-05-05 16:53:36",
                "modified": "2019-05-05 16:55:34",
                "levelTitle": "中高级1"
            },
            {
                "id": 5,
                "created": "2019-05-08 10:33:44",
                "modified": "2019-05-08 10:33:44",
                "levelTitle": "中高级00"
            },
            {
                "id": 6,
                "created": "2019-05-08 10:34:57",
                "modified": "2019-05-08 10:35:20",
                "levelTitle": "中高级123"
            }
        ]
      }

### 课程服务删除 [DELETE] /admin/courseLevels/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Response 204

### 课程增加[POST] /admin/courses
+ Parameters
  + attachmentIds - 非必填字段（添加课程图片）
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
    
      {
    	"data":{
    		"levelId":4,
    		"courseTitle":"孕期瑜伽12期",
    		"thumbnail":"http://static.mifanxing.com/article/image/215/69/0000001.jpg",
    		"description":"此课程适应孕期产妇12",
    		"content":"课程内容11",
    		"recommend":1,
    		"attachmentIds":[1,2,3,4,5,6]
    	 }
      }

+ Response 200 (application/json)

      {
        "data": {
            "id": 13,
            "type": "courses"
        }
      }


### 课程修改 [PUT] /admin/courses/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
        
      {
    	"data":{
    		"levelId":4,
    		"courseTitle":"孕期瑜伽15期",
    		"thumbnail":"http://static.mifanxing.com/article/image/215/69/0000001.jpg",
    		"description":"此课程适应孕期产妇15",
    		"content":"课程内容11",
    		"recommend":1,
    		"attachmentIds":[1,2,3,4,5]
    	}
      }
      
+ Response 200 (application/json)

### 课程详情 [GET] /admin/courses/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)
    
      {
        "data": {
            "id": 14,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-05-08 10:53:35",
            "modified": "2019-05-08 10:54:40",
            "levelId": 4,
            "courseTitle": "孕期瑜伽15期",
            "thumbnail": "http://static.mifanxing.com/article/image/215/69/0000001.jpg",
            "description": "此课程适应孕期产妇15",
            "content": "课程内容11",
            "recommend": 1,
            "pictures": [
                "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420991.jpg",
                "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            ]
        }
      }

### 课程删除 [DELETE] /admin/courses/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Response 204

### 课程列表 [GET] /admin/courses
+ Parameters
  + filter[levelId]=2（课程分类查询）
  + filter[courseTitle:like]=%25孕%25 （'%25'为'%'的转义）
  + page[number]=1&page[size]=10
  + sort -modified(从新到旧) | modified(从旧到新)
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)

      {
        "meta": {
            "totalPages": 1,
            "totalElements": 6,
            "size": 10,
            "number": 1,
            "numberOfElements": 6,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "/admin/courses?page[number]=1&page[size]=10",
            "first": "/admin/courses?page[number]=1&page[size]=10",
            "last": "/admin/courses?page[number]=1&page[size]=10"
        },
        "data": [
            {
                "id": 1,
                "created": "2019-04-10 15:20:05",
                "modified": "2019-04-10 15:20:05",
                "levelId": 3,
                "courseTitle": "产后恢复",
                "levelTitle": "高级"
            },
            {
                "id": 4,
                "created": "2019-04-12 11:22:12",
                "modified": "2019-04-11 11:22:02",
                "levelId": 2,
                "courseTitle": "孕期锻炼",
                "levelTitle": "中级"
            },
            {
                "id": 6,
                "created": "2019-04-12 11:22:16",
                "modified": "2019-04-12 11:22:05",
                "levelId": 1,
                "courseTitle": "产前体检",
                "levelTitle": "初级"
            },
            {
                "id": 7,
                "created": "2019-04-12 11:22:19",
                "modified": "2019-04-12 11:22:09",
                "levelId": 1,
                "courseTitle": "产前锻炼",
                "levelTitle": "初级"
            },
            {
                "id": 13,
                "created": "2019-05-08 10:41:09",
                "modified": "2019-05-08 10:41:09",
                "levelId": 4,
                "courseTitle": "孕期瑜伽12期",
                "levelTitle": "中高级1"
            }
        ]
      }

## 动作管理
+ Data
  + ActionCategory - 动作分类表 
    + categoryTitle (String) - 名称
    + description (String) - 描述
    + enabled (int) - 0禁用 1启用
    + creator (Long) - 创建人
    + modifier (Long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
  + Action - 动作表
    + categoryId (Long) - 分类ID
    + actionTitle (String) - 名称
    + thumbnail (String) - 缩略图
    + description (String) - 描述
    + content (String) - 内容
    + enabled (int) - 0禁用 1启用
    + creator (Long) - 创建人
    + modifier (Long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
    + pictures - 图片
### 动作分类增加[POST] /admin/actionCategories
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
    
      {
    	 "data":{
    	 	 "categoryTitle":"有氧室09",
    		 "description":"室内提供充足的氧气"
    	 }
      }

+ Response 200 (application/json)

      {
        "data": {
            "id": 3,
            "type": "actionCategories"
        }
      }
### 动作分类修改 [PUT] /admin/actionCategories/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
    
      {
    	  "data":{
    		 "categoryTitle":"有氧室08",
    		 "description":"室内提供充足的氧气"
    	  }
      }
+ Response 200 (application/json)

### 动作分类列表 [GET] /admin/actionCategories
+ Parameters
  + filter[categoryTitle:like]=%25氧%25  （'%25'为'%'的转义）
  + page[number]=1&page[size]=10
  + sort -modified(从新到旧) | modified(从旧到新)
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)
    
      {
        "meta": {
            "totalPages": 1,
            "totalElements": 3,
            "size": 10,
            "number": 1,
            "numberOfElements": 3,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "admin/actionCategories?page[number]=1&page[size]=10",
            "first": "admin/actionCategories?page[number]=1&page[size]=10",
            "last": "admin/actionCategories?page[number]=1&page[size]=10"
        },
        "data": [
            {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "categoryTitle": "室内"
            },
            {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-05-06 18:05:35",
                "modified": "2019-05-06 18:06:18",
                "categoryTitle": "有氧室",
                "description": "室内提供充足的氧气"
            },
            {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-05-08 11:13:27",
                "modified": "2019-05-08 11:14:14",
                "categoryTitle": "有氧室08",
                "description": "室内提供充足的氧气"
            }
        ]
      }

### 动作分类删除 [DELETE] /admin/actionCategories/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Response 204


### 动作增加[POST] /admin/actions
+ Parameters
  + attachmentIds - 非必填字段（添加图片）
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
    
      {
    	"data":{
    		"categoryId":2,
    		"actionTitle":"腿部按摩123",
    		"thumbnail":"http://static.mifanxing.com/iyyren/image/201806/06/1638/1111111111.jpg",
    		"description":"腿部锻炼将会缓解肿胀123",
    		"content":"内容部分",
    		"attachmentIds":[1,2,3]
    	}
      }

+ Response 200 (application/json)

      {
        "data": {
            "id": 5,
            "type": "actions"
        }
      }


### 动作修改 [PUT] /admin/actions/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
        
      {
    	 "data":{
    		"categoryId":2,
    		"actionTitle":"腿部按摩1111",
    		"thumbnail":"http://static.mifanxing.com/iyyren/image/201806/06/1638/1111111111.jpg",
    		"description":"腿部锻炼将会缓解肿胀123",
    		"content":"内容部分",
    		"attachmentIds":[1,2,3]
    	 }
      }
      
+ Response 200 (application/json)

### 动作详情 [GET] /admin/actions/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)
    
      {
        "data": {
            "id": 5,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-05-08 11:22:20",
            "modified": "2019-05-08 11:32:29",
            "categoryId": 2,
            "actionTitle": "腿部按摩1111",
            "thumbnail": "http://static.mifanxing.com/iyyren/image/201806/06/1638/1111111111.jpg",
            "description": "腿部锻炼将会缓解肿胀123",
            "content": "内容部分",
            "pictures": [
                "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420991.jpg",
                "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            ]
        }
      }

### 动作删除 [DELETE] /admin/actions/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Response 204

### 动作列表 [GET] /admin/actions
+ Parameters
  + filter[categoryId]=2（动作分类查询）
  + filter[actionTitle:like]=%25部%25 （'%25'为'%'的转义）
  + page[number]=1&page[size]=10
  + sort -modified(从新到旧) | modified(从旧到新)
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)

      {
        "meta": {
            "totalPages": 1,
            "totalElements": 5,
            "size": 10,
            "number": 1,
            "numberOfElements": 5,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "/admin/actions?page[number]=1&page[size]=10",
            "first": "/admin/actions?page[number]=1&page[size]=10",
            "last": "/admin/actions?page[number]=1&page[size]=10"
        },
        "data": [
            {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-16 16:12:00",
                "modified": "2019-04-16 16:11:53",
                "categoryId": 1,
                "actionTitle": "俯卧撑",
                "thumbnail": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg",
                "categoryTitle": "室内"
            },
            {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-16 16:12:03",
                "modified": "2019-04-16 16:11:57",
                "categoryId": 1,
                "actionTitle": "仰卧起坐",
                "thumbnail": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg",
                "categoryTitle": "室内"
            },
            {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-17 09:48:26",
                "modified": "2019-04-17 09:48:24",
                "categoryId": 1,
                "actionTitle": "瑜伽锻炼",
                "thumbnail": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg",
                "categoryTitle": "室内"
            },
            {
                "id": 4,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-05-06 18:13:18",
                "modified": "2019-05-06 18:16:59",
                "categoryId": 2,
                "actionTitle": "腿部按摩1",
                "thumbnail": "http://static.mifanxing.com/iyyren/image/201806/06/1638/1111111111.jpg",
                "description": "腿部锻炼将会缓解肿胀1",
                "content": "内容部分",
                "categoryTitle": "有氧室"
            },
            {
                "id": 5,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-05-08 11:22:20",
                "modified": "2019-05-08 11:32:29",
                "categoryId": 2,
                "actionTitle": "腿部按摩1111",
                "thumbnail": "http://static.mifanxing.com/iyyren/image/201806/06/1638/1111111111.jpg",
                "description": "腿部锻炼将会缓解肿胀123",
                "content": "内容部分",
                "categoryTitle": "有氧室"
            }
        ]
      }

## 孕产知识库管理 
+ Data
  + Knowledge - 孕产知识表 
    + knowledgeTitle (String) - 知识库标题
    + description (String) - 描述
    + content (String) - 知识库内容
    + postUserName (String) - 作者
    + postDate (Date) - 发布时间
    + recommend (int) -是否推荐，0：否，1：是
    + thumbnail (String) - 缩略图
    + enabled (int) - 0禁用 1启用
    + creator (Long) - 创建人
    + modifier (Long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
    + pictures - 图片

### 增加[POST] /admin/knowledges
+ Parameters
  + attachmentIds - 非必填字段（添加图片）
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
    
      {
    	"data":{
    		"knowledgeTitle":"孕期了解Ⅲ",
    		"description":"这是一项在孕期的知识",
    		"content":"一、有好的营养 二、有好的睡眠",
    		"postUserName":"李四",
    		"postDate":"2019-05-06 18:47:30",
    		"recommend":1,
    		"thumbnail":"http://static.mifanxing.com/article/image/215/69/111111.jpg",
    		"attachmentIds":[1,2,3]
    	}
      }

+ Response 200 (application/json)

      {
        "data": {
            "id": 7,
            "type": "Knowledges"
        }
      }


### 修改 [PUT] /admin/knowledges/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
        
      {
    	"data":{
    		"knowledgeTitle":"孕期了解Ⅲ",
    		"description":"这是一项在孕期的知识",
    		"content":"一、有好的营养 二、有好的睡眠asd",
    		"postUserName":"李四",
    		"postDate":"2019-05-06 18:47:30",
    		"recommend":1,
    		"thumbnail":"http://static.mifanxing.com/article/image/215/69/111111.jpg",
    		"attachmentIds":[1,2,3]
    	}
      }
      
+ Response 200 (application/json)

### 详情 [GET] /admin/knowledges/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)
    
      {
        "data": {
            "id": 7,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-05-08 11:43:40",
            "modified": "2019-05-08 11:45:10",
            "knowledgeTitle": "孕期了解Ⅲ",
            "description": "这是一项在孕期的知识",
            "content": "一、有好的营养 二、有好的睡眠asd",
            "postUserName": "李四",
            "postDate": "2019-05-06 18:47",
            "recommend": 1,
            "thumbnail": "http://static.mifanxing.com/article/image/215/69/111111.jpg",
            "pictures": [
                "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420991.jpg",
                "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg",
                "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420993.jpg"
            ]
        }
      }

### 删除 [DELETE] /admin/knowledges/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Response 204

### 列表 [GET] /admin/knowledges
+ Parameters
  + filter[knowledgeTitle:like]=%25部%25 （'%25'为'%'的转义）
  + page[number]=1&page[size]=10
  + sort -modified(从新到旧) | modified(从旧到新)
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)

      {
        "meta": {
            "totalPages": 1,
            "totalElements": 7,
            "size": 10,
            "number": 1,
            "numberOfElements": 7,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "/admin/Knowledges?page[number]=1&page[size]=10",
            "first": "/admin/Knowledges?page[number]=1&page[size]=10",
            "last": "/admin/Knowledges?page[number]=1&page[size]=10"
        },
        "data": [
            {
                "id": 1,
                "created": "2019-05-05 18:47:30",
                "modified": "2019-04-25 10:32:01",
                "knowledgeTitle": "备孕知识"
            },
            {
                "id": 2,
                "created": "2019-05-05 18:47:33",
                "modified": "2019-04-25 10:32:07",
                "knowledgeTitle": "产前知识"
            },
            {
                "id": 3,
                "created": "2019-05-05 18:47:36",
                "modified": "2019-04-25 10:32:09",
                "knowledgeTitle": "产后护理"
            },
            {
                "id": 4,
                "created": "2019-05-05 18:47:39",
                "modified": "2019-04-25 10:32:13",
                "knowledgeTitle": "健康知识"
            },
            {
                "id": 5,
                "created": "2019-05-05 18:57:11",
                "modified": "2019-05-05 18:57:55",
                "knowledgeTitle": "孕期了解1"
            },
            {
                "id": 6,
                "created": "2019-05-06 16:30:32",
                "modified": "2019-05-06 16:33:07",
                "knowledgeTitle": "孕期了解Ⅱ"
            },
            {
                "id": 7,
                "created": "2019-05-08 11:43:40",
                "modified": "2019-05-08 11:45:10",
                "knowledgeTitle": "孕期了解Ⅲ"
            }
        ]
      }

## 活动管理
+ Data
  + Activity - 活动表 
    + activityTitle (String) - 活动标题
    + description (String) - 活动描述
    + content (String) - 活动内容
    + postDate (Date) - 发布时间
    + organizationId (int) - 合作机构id
    + stage (int) - 活动阶段：0：无限制，1：备孕，2：孕期，3：产后，4：早教
    + recommend (int) - 是否推荐，0：否，1：是缩略图
    + hasSign (int) - 是否可以报名；0：否，1：是（默认1可报名）
    + thumbnail(String) - 缩略图
    + enabled (int) - 0禁用 1启用
    + creator (Long) - 创建人
    + modifier (Long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间

### 增加[POST] /admin/activitys
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
    
      {
    	  "data":{
    		 "activityTitle":"月子线下活动123",
    		 "description":"活动描述史蒂芬森123",
    		 "content":"活动内容是的是的所多123",
    		 "organizationId":2,
    		 "stage":1,
    		 "recommend":1,
    		 "hasSign":1,
    		 "thumbnail":"http://static.mifanxing.com/iyyren/image/201806/06/1638/000000.jpg"
    	 }
      }

+ Response 200 (application/json)

      {
         "data": {
             "id": 15,
             "type": "activitys"
         }
      }


### 修改 [PUT] /admin/activitys/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
        
      {
    	 "data":{
    		 "activityTitle":"月子线下活动1234",
    		 "description":"活动描述史蒂芬森1234",
    		 "content":"活动内容是的是的所多1234",
    		 "organizationId":2,
    		 "stage":1,
    		 "recommend":1,
    		 "hasSign":1,
    		 "thumbnail":"http://static.mifanxing.com/iyyren/image/201806/06/1638/000000.jpg"
    	 }
      }
      
+ Response 200 (application/json)

### 详情 [GET] /admin/activitys/details/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)
    
      {
        "data": {
            "id": 15,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-05-08 13:38:15",
            "modified": "2019-05-08 13:41:55",
            "activityTitle": "月子线下活动1234",
            "description": "活动描述史蒂芬森1234",
            "content": "活动内容是的是的所多1234",
            "postDate": "2019-05-08 13:38",
            "organizationId": 2,
            "stage": 1,
            "recommend": 1,
            "hasSign": 1,
            "thumbnail": "http://static.mifanxing.com/iyyren/image/201806/06/1638/000000.jpg",
            "organizationTitle": "月子会所"
        }
      }

### 删除 [DELETE] /admin/activitys/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Response 204

### 列表 [GET] /admin/activitys
+ Parameters
  + filter[activityTitle:like]=%25活动%25 （'%25'为'%'的转义）
  + page[number]=1&page[size]=10
  + sort -modified(从新到旧) | modified(从旧到新)
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)

      {
        "meta": {
            "totalPages": 1,
            "totalElements": 5,
            "size": 10,
            "number": 1,
            "numberOfElements": 5,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "/admin/activitys?page[number]=1&page[size]=10",
            "first": "/admin/activitys?page[number]=1&page[size]=10",
            "last": "/admin/activitys?page[number]=1&page[size]=10"
        },
        "data": [
            {
                "id": 1,
                "created": "2019-04-11 11:41:01",
                "modified": "2019-04-11 11:41:04",
                "activityTitle": "孕妇一日游活动",
                "hasSign": 1,
                "hasSignName": "是"
            },
            {
                "id": 2,
                "created": "2019-04-11 11:41:09",
                "modified": "2019-04-11 11:41:06",
                "activityTitle": "别的地方活动",
                "hasSign": 1,
                "hasSignName": "是"
            },
            {
                "id": 3,
                "created": "2019-04-11 11:41:14",
                "modified": "2019-04-11 11:41:12",
                "activityTitle": "某某活动",
                "hasSign": 0,
                "hasSignName": "否"
            },
            {
                "id": 4,
                "created": "2019-04-11 11:41:22",
                "modified": "2019-04-11 11:41:18",
                "activityTitle": "哈哈活动",
                "hasSign": 1,
                "hasSignName": "是"
            },
            {
                "id": 5,
                "created": "2019-04-11 11:47:34",
                "modified": "2019-04-11 11:47:31",
                "activityTitle": "风儿活动",
                "hasSign": 1,
                "hasSignName": "是"
            }
        ]
      }

## 合作机构管理
+ Data
  + OrganizationCategory - 合作机构分类表 
    + categoryTitle (String) - 标题
    + description (String) - 描述
    + enabled (int) - 0禁用 1启用
    + creator (Long) - 创建人
    + modifier (Long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
  + Organization - 合作机构表 
    + categoryId (int) - 分类id
    + organizationTitle (String) - 机构名称
    + logo (String) - 机构LOGO
    + description (String) - 描述
    + regionId (int) - 区域id
    + address (String) -  详细地址
    + enabled (int) - 0禁用 1启用
    + creator (Long) - 创建人
    + modifier (Long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间

### 合作机构分类增加[POST] /admin/organizationCategories
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
    
      {
    	  "data":{
    	 	 "categoryTitle":"医院",
    		 "description":"内容巴巴多斯岛"
    	 }
      }

+ Response 200 (application/json)

      {
        "data": {
            "id": 3,
            "type": "OrganizationCategory"
        }
      }
### 合作机构分类修改 [PUT] /admin/organizationCategories/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
    
       {
    	  "data":{
    	 	 "categoryTitle":"医院1",
    		 "description":"内容巴巴多斯岛"
    	 }
      }
+ Response 200 (application/json)

### 合作机构分类列表 [GET] /admin/organizationCategories
+ Parameters
  + filter[categoryTitle:like]=%25合作%25 （'%25'为'%'的转义）
  + page[number]=1&page[size]=10
  + sort -modified(从新到旧) | modified(从旧到新)
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)

      {
        "meta": {
            "totalPages": 1,
            "totalElements": 3,
            "size": 10,
            "number": 1,
            "numberOfElements": 3,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "/admin/organizationCategories?page[number]=1&page[size]=10",
            "first": "/admin/organizationCategories?page[number]=1&page[size]=10",
            "last": "/admin/organizationCategories?page[number]=1&page[size]=10"
        },
        "data": [
            {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "categoryTitle": "合作机构分类1"
            },
            {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-05-06 20:09:38",
                "modified": "2019-05-06 20:09:38",
                "categoryTitle": "会所",
                "description": "内容巴巴多斯岛"
            },
            {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-05-06 20:09:45",
                "modified": "2019-05-08 14:00:59",
                "categoryTitle": "医院1",
                "description": "内容巴巴多斯岛"
            }
        ]
      }

### 合作机构分类删除 [DELETE] /admin/organizationCategories/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Response 204

### 合作机构增加[POST] /admin/Organization
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
    
      {
    	 "data":{
    		 "categoryId":3,
    		 "organizationTitle":"上海妇幼保健院",
    		 "logo":"http://static.mifanxing.com/iyyren/image/201806/06/1638/1111111111.jpg",
    		 "description":"腿部锻炼将会缓解肿胀1",
    		 "regionId":3,
    		 "address":"黄浦区苏州路3号"
    	 }
      }

+ Response 200 (application/json)

      {
        "data": {
            "id": 3,
            "type": "Organization"
        }
      }


### 合作机构修改 [PUT] /admin/organizations/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
    
      {
    	 "data":{
    		 "categoryId":3,
    		 "organizationTitle":"上海妇幼保健院1",
    		 "logo":"http://static.mifanxing.com/iyyren/image/201806/06/1638/1111111111.jpg",
    		 "description":"腿部锻炼将会缓解肿胀1",
    		 "regionId":3,
    		 "address":"黄浦区苏州路3号"
    	 }
      }
+ Response 200 (application/json)

### 合作机构详情 [GET] /admin/organizations/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)

      {
        "data": {
            "id": 3,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-05-06 20:16:10",
            "modified": "2019-05-08 14:09:28",
            "categoryId": 3,
            "organizationTitle": "上海妇幼保健院1",
            "logo": "http://static.mifanxing.com/iyyren/image/201806/06/1638/1111111111.jpg",
            "description": "腿部锻炼将会缓解肿胀1",
            "regionId": 3,
            "address": "黄浦区苏州路3号"
        }
      }

### 合作机构删除 [DELETE] /admin/organizations/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Response 204

### 合作机构列表 [GET] /admin/organizations
+ Parameters
  + filter[categoryId]=2（套餐分类查询）
  + filter[organizationTitle:like]=%25会所%25 （'%25'为'%'的转义）
  + page[number]=1&page[size]=10
  + sort -modified(从新到旧) | modified(从旧到新)
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)

      {
        "meta": {
            "totalPages": 1,
            "totalElements": 4,
            "size": 10,
            "number": 1,
            "numberOfElements": 4,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "/admin/organizations?page[number]=1&page[size]=10",
            "first": "/admin/organizations?page[number]=1&page[size]=10",
            "last": "/admin/organizations?page[number]=1&page[size]=10"
        },
        "data": [
            {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "modified": "2019-05-07 15:22:01",
                "categoryId": 1,
                "organizationTitle": "北京月子会所",
                "categoryTitle": "合作机构分类1"
            },
            {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-05-06 20:15:34",
                "modified": "2019-05-08 13:41:55",
                "categoryId": 2,
                "organizationTitle": "月子会所",
                "logo": "http://static.mifanxing.com/iyyren/image/201806/06/1638/1111111111.jpg",
                "description": "腿部锻炼将会缓解肿胀1",
                "regionId": 3,
                "address": "黄浦区苏州路1号",
                "categoryTitle": "会所"
            },
            {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-05-06 20:16:10",
                "modified": "2019-05-08 14:09:28",
                "categoryId": 3,
                "organizationTitle": "上海妇幼保健院1",
                "logo": "http://static.mifanxing.com/iyyren/image/201806/06/1638/1111111111.jpg",
                "description": "腿部锻炼将会缓解肿胀1",
                "regionId": 3,
                "address": "黄浦区苏州路3号",
                "categoryTitle": "医院1"
            },
            {
                "id": 4,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-05-07 13:38:15",
                "modified": "2019-05-07 15:06:02",
                "categoryId": 1,
                "organizationTitle": "方庄妇幼保健院",
                "logo": "https://pics7.baidu.com/feed/0d338744ebf81a4c6746890429f2a85d272da6e0.jpeg?token=3f289d2b9406a768d35",
                "description": "孕妇调养",
                "regionId": 3,
                "address": "北京市丰台区南方庄99号院",
                "categoryTitle": "合作机构分类1"
            }
        ]
      }

## 轮播图管理
+ Data
  + Banner - 轮播图表 
    + attUrl (String) - 图片链接 
    + bannerTitle (String) - banner标题
    + bannerUrl (String) - banner访问路径
    + modular (int) - 模块，0：活动，1：孕产知识，2：课程
    + targetId (Long) - 目标标识
    + enabled (int) - 0禁用 1启用
    + creator (Long) - 创建人
    + modifier (Long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间

### 增加[POST] /admin/banners
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
    
      {
    	 "data":{
    		 "attUrl":"http://static.mifanxing.com/iyyren/image/20 1806/06/1638/00000000000.jpg",
    		 "bannerTitle":"活动开始啦",
    		 "bannerUrl":"localhost:8398/activitys/",
    		 "modular":0,
    		 "targetId":15
    	 }
      }

+ Response 200 (application/json)

      {
        "data": {
            "id": 4,
            "type": "Banner"
        }
      }


### 修改 [PUT] /admin/banners/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Request (application/json)
        
      {
    	 "data":{
    		 "attUrl":"http://static.mifanxing.com/iyyren/image/201806/06/1638/00000000000.jpg",
    		 "bannerTitle":"活动开始啦1",
    		 "bannerUrl":"localhost:8398/activitys/",
    		 "modular":0,
    		 "targetId":15
     	 }
      }
      
+ Response 200 (application/json)

### 详情 [GET] /admin/banners/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)
    
      {
        "data": {
            "id": 4,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-05-08 14:44:23",
            "modified": "2019-05-08 14:47:53",
            "attUrl": "http://static.mifanxing.com/iyyren/image/201806/06/1638/00000000000.jpg",
            "bannerTitle": "活动开始啦1",
            "bannerUrl": "localhost:8398/activitys/",
            "modular": 0,
            "targetId": 15
        }
      }

### 删除 [DELETE] /admin/banners/{id}
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN
+ Response 204

### 列表 [GET] /admin/banners
+ Parameters
  + filter[modular]=id（所属模块查询,id为模块值）
  + page[number]=1&page[size]=10
  + sort -modified(从新到旧) | modified(从旧到新)
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN | ROLE_SUPER_ADMIN

+ Response 200 (application/json)

      {
        "meta": {
            "totalPages": 1,
            "totalElements": 4,
            "size": 10,
            "number": 1,
            "numberOfElements": 4,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "/admin/banners?page[number]=1&page[size]=10",
            "first": "/admin/banners?page[number]=1&page[size]=10",
            "last": "/admin/banners?page[number]=1&page[size]=10"
        },
        "data": [
            {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-28 18:47:10",
                "modified": "2019-04-28 18:46:59",
                "attUrl": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg",
                "bannerTitle": "最新课程",
                "bannerUrl": "localhost:8398/courses/",
                "modular": 2,
                "targetId": 1
            },
            {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-28 18:47:13",
                "modified": "2019-04-28 18:47:02",
                "attUrl": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg",
                "bannerTitle": "最新活动",
                "bannerUrl": "localhost:8398/activitys/",
                "modular": 0,
                "targetId": 1
            },
            {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-04-28 18:47:16",
                "modified": "2019-04-28 18:47:07",
                "attUrl": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg",
                "bannerTitle": "最新孕产知识",
                "bannerUrl": "localhost:8398/knowledges/",
                "modular": 1,
                "targetId": 1
            },
            {
                "id": 4,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-05-08 14:44:23",
                "modified": "2019-05-08 14:47:53",
                "attUrl": "http://static.mifanxing.com/iyyren/image/201806/06/1638/00000000000.jpg",
                "bannerTitle": "活动开始啦1",
                "bannerUrl": "localhost:8398/activitys/",
                "modular": 0,
                "targetId": 15
            }
        ]
      }




