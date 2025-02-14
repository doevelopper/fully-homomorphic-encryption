load("//transpiler:fhe.bzl", "fhe_cc_library")
load("@bazel_skylib//:bzl_library.bzl", "bzl_library")

licenses(["notice"])

fhe_cc_library(
    name = "string_cap_char_tfhe",
    src = "string_cap_char.cc",
    hdrs = ["string_cap_char.h"],
    num_opt_passes = 2,
)

fhe_cc_library(
    name = "string_cap_char_interpreted_tfhe",
    src = "string_cap_char.cc",
    hdrs = ["string_cap_char.h"],
    num_opt_passes = 2,
    transpiler_type = "interpreted_tfhe",
)

fhe_cc_library(
    name = "string_cap_char_bool",
    src = "string_cap_char.cc",
    hdrs = ["string_cap_char.h"],
    num_opt_passes = 2,
    transpiler_type = "bool",
)

cc_binary(
    name = "string_cap_char_tfhe_testbench",
    srcs = [
        "string_cap_char_tfhe_testbench.cc",
    ],
    deps = [
        ":string_cap_char",
        ":string_cap_char_tfhe",
        "//transpiler/data:fhe_data",
        "@com_google_absl//absl/base",
        "@com_google_absl//absl/time",
        "@com_google_xls//xls/common/logging",
        "@com_google_xls//xls/common/status:status_macros",
        "@tfhe//:libtfhe",
    ],
)

cc_binary(
    name = "string_cap_char_interpreted_tfhe_testbench",
    srcs = [
        "string_cap_char_tfhe_testbench.cc",
    ],
    copts = ["-DUSE_INTERPRETED_TFHE"],
    deps = [
        ":string_cap_char",
        ":string_cap_char_interpreted_tfhe",
        "//transpiler/data:fhe_data",
        "@com_google_absl//absl/base",
        "@com_google_absl//absl/time",
        "@com_google_xls//xls/common/logging",
        "@com_google_xls//xls/common/status:status_macros",
        "@tfhe//:libtfhe",
    ],
)

cc_binary(
    name = "string_cap_char_bool_testbench",
    srcs = [
        "string_cap_char.h",
        "string_cap_char_bool_testbench.cc",
    ],
    deps = [
        ":string_cap_char_bool",
        "//transpiler/data:boolean_data",
        "@com_google_absl//absl/container:fixed_array",
        "@com_google_xls//xls/common/logging",
        "@com_google_xls//xls/common/status:status_macros",
    ],
)

cc_library(
    name = "string_cap_char",
    srcs = ["string_cap_char.cc"],
    hdrs = ["string_cap_char.h"],
)

cc_test(
    name = "string_cap_char_test",
    size = "large",
    srcs = ["string_cap_char_test.cc"],
    deps = [
        ":string_cap_char",
        ":string_cap_char_tfhe",
        "//transpiler/data:fhe_data",
        "@com_google_absl//absl/base",
        "@com_google_googletest//:gtest_main",
        "@com_google_xls//xls/common/status:matchers",
        "@tfhe//:libtfhe",
    ],
)
