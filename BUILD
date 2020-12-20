# Bloaty McBloatface, a size profiler for binaries.

proto_library(
    name = "bloaty_proto",
    srcs = ["src/bloaty.proto"],
)

cc_proto_library(
    name = "bloaty_cc_proto",
    deps = [":bloaty_proto"],
)

cc_library(
    name = "bloaty_lib",
    srcs = [
        "src/bloaty.cc",
        "src/bloaty.h",
        "src/demangle.cc",
        "src/demangle.h",
        "src/disassemble.cc",
        "src/dwarf.cc",
        "src/dwarf_constants.h",
        "src/elf.cc",
        "src/macho.cc",
        "src/range_map.cc",
        "src/re.h",
        "src/webassembly.cc",
    ],
    hdrs = [
        "src/bloaty.h",
        "src/range_map.h",
    ],
    copts = ["-fexceptions"],
    deps = [
        ":bloaty_cc_proto",
        "@com_google_protobuf//:protobuf",
        "@com_google_absl//absl/base:core_headers",
        "@com_google_absl//absl/memory",
        "@com_google_absl//absl/numeric:int128",
        "@com_google_absl//absl/strings",
        "@com_google_absl//absl/types:optional",
        "@capstone//:capstone",
        "//third_party/darwin_xnu_macho",
        "//third_party/freebsd_elf",
        "@com_googlesource_code_re2//:re2",
    ],
)

cc_binary(
    name = "bloaty",
    srcs = ["src/main.cc"],
    visibility = ["//visibility:public"],
    deps = [
        ":bloaty_cc_proto",
        ":bloaty_lib",
    ],
)

cc_binary(
    name = "bloaty_test",
    testonly = 1,
    srcs = [
        "tests/bloaty_test.cc",
        "tests/strarr.h",
        "tests/test.h",
    ],
    deps = [
        ":bloaty_cc_proto",
        ":bloaty_lib",
        "//net/proto2/public:proto2",
        "//testing/base/public:gunit_main",
        "//third_party/absl/strings",
    ],
)

cc_binary(
    name = "bloaty_misc_test_binary",
    testonly = 1,
    srcs = [
        "tests/bloaty_misc_test.cc",
        "tests/strarr.h",
        "tests/test.h",
    ],
    deps = [
        ":bloaty_cc_proto",
        ":bloaty_lib",
        "//net/proto2/public:proto2",
        "//testing/base/public:gunit_main",
        "//third_party/absl/strings",
    ],
)

cc_test(
    name = "range_map_test",
    srcs = ["tests/range_map_test.cc"],
    copts = ["-fexceptions"],
    features = ["-use_header_modules"],  # Incompatible with -fexceptions.
    deps = [
        ":bloaty_lib",
        "@com_google_googletest//:gtest_main",
    ],
)

filegroup(
    name = "testdata",
    srcs = glob([
        "tests/testdata/**/*.o",
        "tests/testdata/**/*.a",
        "tests/testdata/**/*.so",
        "tests/testdata/**/*.bin",
    ]),
)

sh_test(
    name = "bloaty_test-linux_x86-64",
    srcs = ["tests/bloaty_test.sh"],
    args = [
        "bloaty_test",
        "linux-x86_64",
    ],
    data = [
        ":bloaty_test",
        ":testdata",
    ],
)

sh_test(
    name = "bloaty_test_linux_x86",
    srcs = ["tests/bloaty_test.sh"],
    args = [
        "bloaty_test",
        "linux-x86",
    ],
    data = [
        ":bloaty_test",
        ":testdata",
    ],
)

sh_test(
    name = "bloaty_misc_test",
    srcs = ["tests/bloaty_test.sh"],
    args = [
        "bloaty_misc_test_binary",
        "misc",
    ],
    data = [
        ":bloaty_misc_test_binary",
        ":testdata",
    ],
)
