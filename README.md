# -Scores-Management
1、需求分析
1.1数据流图
1.1.1顶层图


1.1.2一层图

说明：课程成绩管理系统细化成1.成绩管理；2.成绩查询；3.成绩统计三个子系统（子加工）


1.1.3二层图
对加工1成绩管理的细化

对加工2成绩查询的细化

对加工3成绩统计的细化



1.2数据字典
1.2.1数据流描述：
学生成绩统计表
名称：学生成绩统计表
别名：无
描述：用于给出学生成绩的统计信息
数据流组成：学生成绩统计表=教师名称+教师代码+课程名称+课程代码+学生成绩平均分+学生成绩最高分+学生成绩最低分+学生成绩优秀率+学生成绩良好率+学生成绩不及格率
数据流来源：加工3成绩统计
数据流去向：教师

1.2.2文件描述
（1）课堂点名成绩记录
文件名称：课堂点名成绩记录
别名：无
简述：给出学生课堂点名成绩记录
写文件加工：加工1成绩管理
读文件加工：加工3成绩查询
文件组成：课堂点名成绩=学生姓名+学号+课程名称+课程代码+第一次课堂点名成绩+第二次课堂点名成绩+第三次课堂点名成绩+教师名称+教师代码
（2）课堂考试成绩记录
文件名称：课堂考试成绩记录
别名：无
简述：给出学生课堂考试成绩记录
写文件加工：加工1成绩管理
读文件加工：加工3成绩查询
文件组成：课堂考试成绩记录=学生姓名+学号+课程名称+课程代码+第一次课堂考试成绩+第二次课堂考试成绩+第三次课堂考试成绩+教师名称+教师代码
（3）课后作业成绩记录
文件名称：课后作业成绩记录
别名：无
简述：给出学生课后作业成绩记录
写文件加工：加工1成绩管理
读文件加工：加工3成绩查询
文件组成：课后作业成绩记录=学生姓名+学号+课程名称+课程代码+第一次课后作业成绩+第二次课后作业成绩+第三次课后作业成绩+教师名称+教师代码
（4）期末考试成绩记录
文件名称：期末考试成绩记录
别名：无
简述：给出学生期末考试成绩记录
写文件加工：加工1成绩管理
读文件加工：加工3成绩查询
文件组成：期末考试成绩记录=学生姓名+学号+课程名称+课程代码+期末考试成绩+教师名称+教师代码
（5）学生个人成绩记录
文件名称：学生个人成绩记录
别名：无
简述：给出学生个人成绩记录
写文件加工：加工1成绩管理
读文件加工：加工3成绩查询
文件组成：期末考试成绩记录=学生姓名+学生学号+教师名称+教师代码+课程名称+课程代码+课堂点名成绩+课堂考试成绩+课后作业成绩+期末考试成绩+总评成绩




1.3ER分析
实体：学生、个人成绩表
联系：学生修读课程记录、学生成绩统计表


1.4加工规约
1.4.1录入成绩
名称：录入成绩
别名：无
加工号：1.1
简述：将符合要求的学生成绩录入系统
输入数据流：待录学生成绩
输出数据流：学生成绩
加工逻辑：录入成绩包括课堂点名成绩、课堂考试成绩、课后作业成绩各三次，以及一次期末考试成绩。对每个学生的成绩，必须先添加学生的学号。每项成绩利用百分制录入，不能为负数，点名用0和100分别表示缺课和未缺课。
异常处理：若不符合要求则给出错误信息
加工激发条件：教师选择了成绩管理的添加学生成绩功能

1.4.2修改成绩
名称：修改成绩
别名：无
加工号：1.2
简述：将符合要求的学生成绩在系统修改
输入数据流：待修改学生成绩
输出数据流：学生成绩
加工逻辑：根据学号，修改对应学生各次课堂点名成绩、课堂考试成绩、课后作业成绩，以及一次期末考试成绩。对每个学生的成绩，必须先添加学生的学号。每项成绩利用百分制进行修改，不能为负数，点名用0和100分别表示缺课和未缺课。确认后保存修改的信息。
异常处理：若不符合要求则给出错误信息
加工激发条件：教师选择了成绩管理的修改学生成绩功能


1.4.3删除成绩
名称：删除成绩
别名：无
加工号：1.3
简述：删除对应学生成绩
输出数据流：无
加工逻辑：根据学号，删除对应学生成绩。在系统提示操作风险时可取消删除操作，若确认删除后系统删除改学生的信息。
异常处理：若不存在学号对应的学生，则给出错误信息
加工激发条件：教师选择了成绩管理的删除学生成绩功能

1.4.4成绩查询
名称：成绩查询
别名：无
加工号：2
简述：对某个学生某课程的成绩情况作出统计显示
输入数据流：学生学号
输出数据流：学生成绩表
加工逻辑：以学生学号为查询关键字，在学生成绩统计表中查询学生姓名、每门课程名称、课程代号、教师名称、教师代号及各项成绩。其中总成绩为各项成绩录入后，系统自动根据各项成绩在总成绩中所占比例计算出来。
异常处理：若不存在查询学生的学号，则给出相应提示信息 
加工激发条件：学生或教师进行了相应的界面操作后

1.4.5成绩统计
名称：成绩统计
别名：无
加工号：3
简述：对某课程的所有学生成绩情况作出统计和分析。
输入数据流：无
输出数据流：学生成绩统计表
加工逻辑：以课程代号、教师名称和教师代号为统计分析时的查询关键字，在学生成绩表中查询每门课程名称和总成绩的值，再计算成绩的平均分、最高分、最低分、优秀率、良好率、不及格率的值。
异常处理：若查询结果为空则给出相应提示信息 
加工激发条件：教师进行了成绩统计界面操作后
.。。。
