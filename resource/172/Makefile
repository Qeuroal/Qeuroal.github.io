# 使用说明
# 所有文件需要位于当前目录下
# 含有主函数的命名规则: *_main.c or *_main.cpp
# 测试文件的命名规则: *tmp*.c or *tmp*.cpp
# 编译参数使用: opts, 如: make opts=-g\ -Wall

mainfile ?= main.cpp

CC := g++

C_FLAGS := -g -Wall
C_FLAGS += $(opts)
C_ALL_FILES := $(wildcard *.c)
C_MAIN_FILES := $(wildcard *main.c)
C_TMP_FILE := $(wildcard *tmp*.c)
C_FILES := $(filter-out $(C_MAIN_FILES) $(C_TMP_FILE), $(C_ALL_FILES))
C_FILES += $(mainfile)
C_OBJS := $(patsubst %.c,%.o,$(C_FILES))

CPP_FLAGS := -g -Wall
CPP_FLAGS += $(opts)
CPP_ALL_FILES := $(wildcard *.cpp)
CPP_MAIN_FILES := $(wildcard *main.cpp)
CPP_TMP_FILE := $(wildcard *tmp*.cpp)
CPP_FILES := $(filter-out $(CPP_MAIN_FILES) $(CPP_TMP_FILE), $(CPP_ALL_FILES))
CPP_FILES += $(mainfile)
CPP_OBJS := $(patsubst %.cpp,%.o,$(CPP_FILES))

demo: $(CPP_OBJS)
	$(CC) -o demo $(CPP_FLAGS) $(CPP_OBJS)

%.o: %.cpp
	g++ -c $(CPP_FLAGS) $< -o $@

%.o: %.c
	gcc -c $(C_FLAGS) $< -o $@

.PHONY: clean
clean:
	rm -f *.o
	rm -f demo
