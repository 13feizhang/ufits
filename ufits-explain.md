### 针对学员端状态红点数据查询

 + 说明：
   + A 数据存储于redis；
   + B 过期时间：12小时；
   + C 有新值时查到值为 "new", 没查到或值为 "old" 说明没新值；
   + D 查到后需将值改为 "old" 

 + 对应的键为：
 + 我的订单
   + key: "ufits:myorder:" + studentId

 + 我的课程
   + key："ufits:mycourse:" + studentId

 + 我的老师
   + key: "ufits:myteacher:" + studentId

 + 我的作业
   + key: "ufits:myhomework:" + studentId

 + 我的预约
    + key: "ufits:myreservation:" + studentId

 + 请假申请
    +  key: "ufits:leaveApply:" + studentId
 
 +  我的改变
   + key: "ufits:mychange:" + studentId

 +  评估方案
   + key: "ufits:evaluationplane:" + studentId




