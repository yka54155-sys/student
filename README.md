# 学生管理系统 (Student Management System)

一个基于C++和SQLite3开发的命令行学生管理系统，提供学生信息管理和成绩管理功能。

## 功能特性

- 📚 **学生信息管理**
  - 添加学生信息（ID、姓名、年龄）
  - 删除学生信息
  - 修改学生信息
  - 按姓名查找学生
  - 按ID查找学生
  - 显示所有学生信息

- 📊 **成绩管理**
  - 添加科目和成绩
  - 修改学生成绩
  - 查询学生成绩
  - 计算所有学生平均分
  - 按总分排序（升序/降序）
  - 显示最高分和最低分学生
  - 查询不及格学生（平均分<60）

## 项目结构

```
student/
├── bin/                    # 可执行文件和数据库
│   ├── Student.exe         # 主程序
│   ├── Student.db          # SQLite数据库
│   ├── libsqlite3_dll.dll  # SQLite动态库
│   └── libSQLite3Cpp_dll.dll
├── build/                  # CMake构建文件
├── include/                # 头文件
│   ├── Class.hpp
│   ├── Head.hpp
│   ├── Include.hpp
│   ├── Menu.hpp
│   ├── sqlite3cpp.hpp
│   └── Student_callback.hpp
├── lib/                    # 静态库文件
│   ├── libsqlite3_lib.a
│   └── libSQLite3Cpp_lib.a
├── src/                    # 源代码
│   ├── class.cpp
│   ├── head.cpp
│   ├── main.cpp
│   ├── menu.cpp
│   └── student_callback.cpp
├── sqlite/                 # SQLite封装库
├── build.bat               # 构建脚本
├── run.bat                 # 运行脚本
├── CMakeLists.txt          # CMake配置文件
└── README.md               # 项目说明文档
```

## 技术栈

- **编程语言**: C++
- **数据库**: SQLite3
- **构建工具**: CMake
- **编译器**: MinGW (Windows)
- **SQLite封装**: 自定义sqlite3cpp库

## 快速开始

### 环境要求

- Windows操作系统
- MinGW编译器
- CMake 4.0或更高版本

### 构建和运行

1. **构建项目**
   ```bash
   build.bat
   ```
   此命令将自动构建项目并将可执行文件输出到`bin`目录。

2. **运行程序**
   ```bash
   run.bat
   ```
   或者直接运行：
   ```bash
   cd bin
   Student.exe
   ```

### 手动构建

如果需要手动构建，请按以下步骤操作：

```bash
# 创建构建目录
mkdir build
cd build

# 生成Makefile
cmake .. -G "MinGW Makefiles"

# 编译项目
cmake --build .

# 返回根目录
cd ..
```

## 数据库结构

系统使用SQLite数据库存储数据，包含以下表：

### student表
| 字段 | 类型 | 约束 | 描述 |
|------|------|------|------|
| ID | TEXT | PRIMARY KEY | 学生ID |
| NAME | TEXT | NOT NULL | 学生姓名 |
| AGE | INT | NOT NULL | 学生年龄 |
| TOTAL_SCORE | REAL | - | 总分（自动计算） |
| AVERAGE_SCORE | REAL | - | 平均分（自动计算） |

### score表
| 字段 | 类型 | 约束 | 描述 |
|------|------|------|------|
| ID | TEXT | PRIMARY KEY | 学生ID |
| SUBJECT | TEXT | PRIMARY KEY | 科目名称 |
| SCORE | DOUBLE | - | 科目成绩 |

## 使用说明

1. 运行程序后，会显示主菜单
2. 输入对应数字选择功能
3. 按照提示输入相关信息
4. 输入0或无效数字可退出程序

## 注意事项

- 首次运行时会自动创建数据库和表结构
- 每个学生的ID必须唯一
- 默认包含语文、数学、英语三个科目
- 总分和平均分会自动计算和更新
- 数据库文件`Student.db`位于`bin`目录下

## 开发者信息

- 项目使用C++17标准
- 采用面向对象设计
- 使用SQLite3进行数据持久化
- 支持中文显示（UTF-8编码）

## 许可证

本项目采用MIT许可证。
