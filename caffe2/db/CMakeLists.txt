set(Caffe2_DB_COMMON_CPU_SRC
    "${CMAKE_CURRENT_SOURCE_DIR}/create_db_op.cc"
    "${CMAKE_CURRENT_SOURCE_DIR}/protodb.cc"
)
set(Caffe2_DB_COMMON_GPU_SRC
    "${CMAKE_CURRENT_SOURCE_DIR}/create_db_op_gpu.cc"
)
set(Caffe2_DB_COMMON_HIP_SRC
    "${CMAKE_CURRENT_SOURCE_DIR}/hip/create_db_op_hip.cc"
)

# Common files that are always going to be included.
list(APPEND Caffe2_CPU_SRCS ${Caffe2_DB_COMMON_CPU_SRC})
list(APPEND Caffe2_GPU_SRCS ${Caffe2_DB_COMMON_GPU_SRC})
list(APPEND Caffe2_HIP_SRCS ${Caffe2_DB_COMMON_HIP_SRC}) 

# DB specific files
if (USE_LMDB)
  list(APPEND Caffe2_CPU_SRCS "${CMAKE_CURRENT_SOURCE_DIR}/lmdb.cc")
endif()

if (USE_LEVELDB)
  list(APPEND Caffe2_CPU_SRCS "${CMAKE_CURRENT_SOURCE_DIR}/leveldb.cc")
endif()

if (USE_ZMQ)
  list(APPEND Caffe2_CPU_SRCS "${CMAKE_CURRENT_SOURCE_DIR}/zmqdb.cc")
endif()

set(Caffe2_CPU_SRCS ${Caffe2_CPU_SRCS} PARENT_SCOPE)
set(Caffe2_GPU_SRCS ${Caffe2_GPU_SRCS} PARENT_SCOPE)
set(Caffe2_HIP_SRCS ${Caffe2_HIP_SRCS} PARENT_SCOPE)
