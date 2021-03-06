## 用户表
- id
- name
- account
- password
- room 已分配的宿舍，如果没分配宿舍就默认为空

### 宿舍表（所有喜好字段都是集合）
- id
- peopleNum 当前人数 (6人为满员)
- getUpTime 起床时间段（一个数组，存放两个时间段，比如[09:00, 09:59]） [数组]
- sleepTime 睡觉时间段，同上 [数组]
- game 喜欢的游戏类型 [数组]
- read 喜欢的阅读类型 [数组]
- video 喜欢影视作品类型 [数组]
- sport 喜欢的运动类型 [数组]
- music 喜欢的音乐类型 [数组]
- religion 是否信奉宗教？ [数组]
- quite 是否希望有一个安静的环境？ [数组]
- noise 是否会在宿舍经常有产生噪音的行为？ [数组]
- sound 是否习惯使用公放设备（如使用外置音响）？ [数组]
- stay 是否会经常长时间待在宿舍？ [数组]

## 调查问卷表（所有喜好字段都是集合）
- id
- uid
- getUpTime [字符串]
- sleepTime [字符串]
- game 喜欢的游戏类型 [数组]
- read 喜欢的阅读类型 [数组]
- video 喜欢影视作品类型 [数组]
- sport 喜欢的运动类型 [数组]
- music 喜欢的音乐类型 [数组]
- religion 是否信奉宗教？ ["0"或"1"]
- quite 是否希望有一个安静的环境？ ["0"或"1"]
- noise 是否会在宿舍经常有产生噪音的行为？ ["0"或"1"]
- sound 是否习惯使用公放设备（如使用外置音响）？ ["0"或"1"]
- stay 是否会经常长时间待在宿舍？ ["0"或"1"]

关于起床时间和睡眠时间的筛选分以下几步（假如用户A选择了09:32起床，00:00睡觉）：
1. 筛选出getUpTime时间为[9:00, 09:59]的宿舍。
2. 筛选出sleepTime时间为[00:00, 00:59]的宿舍。
3. 如果存在一步未筛选出宿舍，就新建一个宿舍，getUpTime字段的数据为[9:00, 09:59]，sleepTime字段的数据为[00:00, 00:59]。


## 反馈表
- id
- uid
- roomId
- harmonious 和谐度评分（1-5）
- comment 宿舍评价
