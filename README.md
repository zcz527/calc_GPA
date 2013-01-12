<head><meta charset="UTF-8"></head>
# 计算学分基点和获取四六级成绩

### 计算学分基点公式：

`学分基点=∑(课程成绩*课程学分)/应修学分`

### 计算细节：

- 全校性公选课不参与学分绩点计算
- 选修课参与学分计算
- 二级学分计算方法：合格：60分，不合格0分
- 五级学分计算方法：优秀95分，良好84分，中等73分，及格62分，不及格0分
- 双学位按照正常科目参与计算
- 重修通过科目按照正常考试科目计算
- 补考通过科目成绩按照六十分计算，学分按照原学分计算。
- 重修科目一次考试未通过，补考通过计算方法相同
- 缺考，禁考，退学，缓考，休学，作弊等成绩按0分，学分计入应修学分
- 免修科目成绩按60分计算
- 第一次考试成绩小于60分按0分计算,补考通过科目成绩按照六十分计算，学分计入应修学分
- 上面的计算方法如有错误，请发邮件至：ma6174#163.com (#换成@)

### 实现方法：
用python模拟提交数据，获取成绩信息页面，再用正则表达式匹配需要的信息，包括课程名称，课程类型，成绩，基点等信息，根据学分基点计算公式进行计算，返回计算结果。

### 使用说明：
1. 创建一个对象`gpa = GPA("学号")`
- 计算学分基点：`gpa.get_gpa()`
- 返回值：出错的话返回`-1`,正确的话返回一个字典。

字典说明：

    {
        "id":           学号,字符串
        "name":         姓名,字符串
        "sex":          性别,字符串
        "year":         年级,字符串
        "collage":      学院,字符串
        "major":        专业,字符串
        "Class":        班级,字符串
        "stu_len":      学制,字符串
        "level":        层次,字符串
        "foreign":      外语,字符串
        "type":         课程类别，列表（每门课程的类别）
        "course":       课程名称,列表(每门课程的名称)
        "credits":      学分,列表(每门课程的学分)
        "score":        成绩,列表(每门课程的成绩)
        "score2":       补考成绩,列表(每门课程的补考成绩)
        "second":       是否是第二专业,列表
        "ave_score":    平均学分基点,浮点数
        "totle_score":  总成绩,浮点数
        "totle_credits":总学分,浮点数
        "not_accept":   至今未通过科目,列表
    }

### 查询四六级成绩方法：
该成绩从学校网站获得，多次考试的话有多次成绩

- 创建一个对象：`cet = CET()`
- 查询：`cet.get_cet_dict('你的学号')`

返回值：失败的话返回-1,成功返回一个字典：

字典说明：

    {
        "id":           学号,字符串
        "name":         姓名,字符串
        "sex":          性别,字符串
        "year":         年级,字符串
        "collage":      学院,字符串
        "class":        班级,字符串
        "foreign":      外语,字符串
        "total":        四六级考试次数,整型数
        "cet_num":      每次四六级考试的考号，列表
        "cet_time":     每次四六级考试的时间，列表
        "cet_type":     每次四六级考试的类型（四级还是六级），列表
        "cet_score":    每次四六级考试的成绩，列表
    }

### 获取最新四六级成绩：

这个四六级成绩是从官网获得，主要用于刚出成绩但是学校网站还没更新的情况。

- 创建一个对象:`cet = CET()`
- 查询：`cet.get_last_cet_score("你的考号","你的姓名")`

返回值：失败的话返回-1,成功返回一个字典

字典说明：

	{
		"num":      考号，字符串,
		"name":     姓名,字符串,
		"school":   学校，字符串
		"type":     类型（四级还是六级），字符串
		"time":     考试时间,字符串
		"total":    总分,字符串
		"listen":   听力成绩,字符串
		"read":     阅读成绩,字符串
		"mix":      综合成绩,字符串
		"write":    写作成绩,字符串
	}
