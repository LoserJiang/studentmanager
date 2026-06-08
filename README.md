# 学生信息管理系统

基于 **JSP + Servlet + JavaBean** 实现的MVC架构学生信息管理系统，支持学生信息的增删改查以及Excel批量导入功能。

## 项目简介

本项目是一个典型的Java Web应用，采用MVC设计模式，实现了学生信息的完整管理功能。通过本项目的开发，掌握了JSP、Servlet、JavaBean技术的综合运用，以及MVC三层架构的设计思想。

## 技术栈

| 技术 | 版本 | 说明 |
|------|------|------|
| JDK | 17 | Java开发环境 |
| Tomcat | 10.1.55 | Web应用服务器 |
| MySQL | 8.0 | 数据库 |
| Servlet | 6.0 | 控制器层 |
| JSP | 3.1 | 视图层 |
| Eclipse | 2023-09 | 开发工具 |
| Apache POI | 3.17 | Excel处理 |

## 功能列表

- ✅ 学生信息列表展示
- ✅ 新增学生信息
- ✅ 修改学生信息
- ✅ 删除学生信息
- ✅ Excel文件批量导入学生数据

## 项目结构
studentmanager/
├── src/main/java/
│ ├── control/ # 控制器层（Servlet）
│ │ ├── ListStudentServlet.java
│ │ ├── InsertStudentServlet.java
│ │ ├── DoInsertStudentServlet.java
│ │ ├── ShowUpdateStudentServlet.java
│ │ ├── DoUpdateStudentServlet.java
│ │ ├── DeleteStudentServlet.java
│ │ └── ImportExcelServlet.java
│ ├── model/ # 模型层（业务逻辑）
│ │ └── StudentModel.java
│ ├── entity/ # 实体类
│ │ └── Student.java
│ └── dbutil/ # 数据库工具类
│ └── Dbconn.java
└── src/main/webapp/
├── jsp/ # 视图层（JSP）
│ ├── studentlist.jsp
│ ├── studentinsert.jsp
│ ├── studentupdate.jsp
│ └── upload.jsp
└── WEB-INF/
└── web.xml

## 数据库设计

### 数据库名：students

### 数据表：student

| 字段名 | 类型 | 说明 | 约束 |
|--------|------|------|------|
| id | INT | 主键ID | PRIMARY KEY, AUTO_INCREMENT |
| student_id | VARCHAR(20) | 学号 | NOT NULL, UNIQUE |
| name | VARCHAR(50) | 姓名 | NOT NULL |
| gender | VARCHAR(10) | 性别 | |
| age | INT | 年龄 | |
| major | VARCHAR(100) | 专业 | |
| grade | VARCHAR(20) | 年级 | |

### 建表SQL

```sql
CREATE DATABASE IF NOT EXISTS students;
USE students;

CREATE TABLE IF NOT EXISTS student (
    id INT PRIMARY KEY AUTO_INCREMENT,
    student_id VARCHAR(20) NOT NULL UNIQUE,
    name VARCHAR(50) NOT NULL,
    gender VARCHAR(10),
    age INT,
    major VARCHAR(100),
    grade VARCHAR(20)
);
环境配置
1. 导入项目
bash
git clone https://github.com/你的用户名/studentmanager-mvc.git
2. 配置数据库
修改 src/main/java/dbutil/Dbconn.java 中的数据库用户名和密码：

java
private static final String USER = "root";
private static final String PASSWORD = "你的密码";
3. 添加JAR包
将以下jar包放入 src/main/webapp/WEB-INF/lib 目录：

mysql-connector-j-8.0.31.jar

poi-3.17.jar

poi-ooxml-3.17.jar

poi-ooxml-schemas-3.17.jar

xmlbeans-2.6.0.jar

commons-collections4-4.1.jar

4. 部署运行
将项目部署到 Tomcat 10.1.55

启动Tomcat服务器

访问：http://localhost:8080/studentmanager/ListStudentServlet.do

Excel导入模板
学号	姓名	性别	年龄	专业	年级
20210001	张三	男	20	计算机科学与技术	2021级
20210002	李四	女	19	软件工程	2021级
