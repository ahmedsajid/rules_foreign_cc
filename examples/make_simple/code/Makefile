BUILD_DIR=build-out

UNAME:=$(shell uname)

ifneq (,$(findstring NT, $(UNAME)))
  # If Windows
  CXXFLAGS := $(CXXFLAGS) /MD
else
  CXXFLAGS := $(CXXFLAGS) -fPIC
endif

default all $(BUILD_DIR)/lib/liba.a: liba.cpp liba.h
	rm -rf $(BUILD_DIR)/lib
	mkdir -p $(BUILD_DIR)/lib
	$(CXX_WRAPPER) $(CXXFLAGS) -o $(BUILD_DIR)/lib/liba.o -c liba.cpp
	ar rcs $(BUILD_DIR)/lib/liba.a $(BUILD_DIR)/lib/liba.o

install: $(BUILD_DIR)/lib/liba.a
	mkdir -p $(PREFIX)/lib $(PREFIX)/include
	cp -rpv $(BUILD_DIR)/lib $(PREFIX)
	cp -p liba.h $(PREFIX)/include
