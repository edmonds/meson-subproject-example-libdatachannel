project(
  'example',
  'c',
  'cpp',
  version: '0.1.0',
  meson_version: '>=1.0.0',
  default_options: [
    'b_lto=true',
    'buildtype=debugoptimized',
    'c_std=gnu17',
    'cpp_std=c++20',
    'warning_level=2',
    'werror=false',
    'wrap_mode=forcefallback',
  ]
)

cmake = import('cmake')
libdatachannel_cmake_subproj = cmake.subproject('libdatachannel')
message('Available CMake targets in libdatachannel_subproj:\n - ' + '\n - '.join(libdatachannel_cmake_subproj.target_list()))

libdatachannel  = libdatachannel_cmake_subproj.dependency('datachannel-static')
juice           = libdatachannel_cmake_subproj.dependency('juice-static')
nlohmann_json   = libdatachannel_cmake_subproj.dependency('nlohmann_json')
srtp2           = libdatachannel_cmake_subproj.dependency('srtp2')
usrsctp         = libdatachannel_cmake_subproj.dependency('usrsctp')

libdatachannel_dependencies = [
  libdatachannel,
  juice,
  nlohmann_json,
  srtp2,
  usrsctp,
]

executable('streamer',
  [
    'src/streamer/ArgParser.cpp',
    'src/streamer/dispatchqueue.cpp',
    'src/streamer/fileparser.cpp',
    'src/streamer/h264fileparser.cpp',
    'src/streamer/helpers.cpp',
    'src/streamer/main.cpp',
    'src/streamer/opusfileparser.cpp',
    'src/streamer/stream.cpp',
  ],
  dependencies: libdatachannel_dependencies,
  install: true)
