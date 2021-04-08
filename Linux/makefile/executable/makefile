### @author 
### @brief

CC:=gcc
CXX:=g++
LD:=ld
AR=ar

CFLAGS+=-g -Wall -I ./include\
-I ../../../Agent/include\
-I ../../../../../ThirdPartyProjects/PJSIP/pjproject-2.7/pjlib/include\
-I ../../../../../ThirdPartyProjects/PJSIP/pjproject-2.7/pjlib-util/include\
-I ../../../../GatewayCommLib/GatewayCommLib/include

LDFLAGS+= -L /usr/lib64\
-L ../../../Agent/lib\
-L ../../../../../ThirdPartyProjects/PJSIP/pjproject-2.7/pjlib/lib\
-L ../../../../../ThirdPartyProjects/PJSIP/pjproject-2.7/pjlib-util/lib\
-L ../../../../GatewayCommLib/GatewayCommLib/lib

LIBS=-lpthread -lstdc++ -luuid\
-lGatewayComm\
-lAgent\
-lpj-x86_64-unknown-linux-gnu\
-lpjlib-util-x86_64-unknown-linux-gnu

#SHARE+=
#shared lib
#SHARE+=-fPIC -share

TARGET_DIR=./bin
SRC_ROOT=./src
OBJ_DIR=./obj

vpath %.cpp src
vpath %.c src
vpath %.h include

#find out all (sub)directories inside the $(SRC_ROOT)
SRC_DIRS=$(shell find $(SRC_ROOT) -type d)

#.cpp or .c source file paths. e.g. src/main.cpp src/math/Calc.c
CPP_SRC_PATHS=$(foreach dir, $(SRC_DIRS), $(wildcard $(dir)/*.cpp))
C_SRC_PATHS=$(foreach dir, $(SRC_DIRS), $(wildcard $(dir)/*.c))

#object files that not including any directory prefix. e.g. main.o test.o
CPP_OBJS=$(foreach cpp_file, $(notdir $(CPP_SRC_PATHS)), $(patsubst %.cpp, %.o, $(cpp_file)))
C_OBJS=$(foreach c_file, $(notdir $(C_SRC_PATHS)), $(patsubst %.c, %.o, $(c_file)))

#object file output paths. e.g. ./obj/main.o ./obj/test.o
CPP_OBJ_OUT_PATHS=$(addprefix $(OBJ_DIR)/, $(CPP_OBJS))
C_OBJ_OUT_PATHS=$(addprefix $(OBJ_DIR)/, $(C_OBJS))

#main target
TARGET=$(TARGET_DIR)/ClientAgentTest

#echo:
#	@echo "\n"
#	@echo $(SRC_DIRS)
#	@echo ".cpp: " $(CPP_SRC_PATHS)


$(TARGET):$(CPP_OBJ_OUT_PATHS) $(C_OBJ_OUT_PATHS)
	@if [ ! -d $(TARGET_DIR) ]; then mkdir -p $(TARGET_DIR); fi;
	$(CXX) -o $@ $^ $(LDFLAGS) $(LIBS)

	
$(OBJ_DIR)/%.o : %.cpp
	@if [ ! -d $(OBJ_DIR) ]; then mkdir -p $(OBJ_DIR); fi;
	$(CXX) $(CFLAGS) -c $^ -o $@
	
$(OBJ_DIR)/%.o : %.c
	@if [ ! -d $(OBJ_DIR) ]; then mkdir -p $(OBJ_DIR); fi;
	$(CC) $(CFLAGS) -c $^ -o $@

clean:
	rm -f $(OBJ_DIR)/*.o $(TARGET)