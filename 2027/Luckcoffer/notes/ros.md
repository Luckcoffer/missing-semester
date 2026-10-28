#自定义信息
##在功能包中创建msg文件夹
创建.msg来创建自定义信息
```
string name
uint16 agee
```
##改配置文件
1. package.xml
``` msg
<build_depend>message_generation</build_depend>
<exec_depend>message_runtime</exec_depend>
```
message/_generation：编译阶段用，将.msg生成C++/python代码
message/_runtime：程序运行阶段用

`CmakeList.txt
``` 
find_package(
	message_generation
)

add_message_files(
  FILES
  Person.msg
)

generate_messages(
  DEPENDENCIES
  std_msgs		#声明依赖std_msgs
)

# 运行依赖加入message_runtime
catkin_package(
  CATKIN_DEPENDS roscpp rospy std_msgs message_runtime
)
```
