package(default_visibility = ["//visibility:public"])

load("@io_bazel_rules_closure//closure:defs.bzl", "closure_js_library")
load("@org_tensorflow_tensorboard//tensorboard/defs:web.bzl", "ts_web_library")
load("@org_tensorflow_tensorboard//tensorboard/defs:vulcanize.bzl", "tensorboard_html_binary")

licenses(["notice"])  # Apache 2.0

closure_js_library(
    name = "externs",
    srcs = ["externs.js"],
)

ts_web_library(
    name = "test",
    srcs = [
        "feature_statistics_generator_test.ts",
        "overview_data_model_test.ts",
        "utils_test.ts",
        "test.html",
    ],
    clutz_entry_points = [
        "proto.featureStatistics.DatasetFeatureStatistics",
        "proto.featureStatistics.DatasetFeatureStatisticsList",
        "proto.featureStatistics.FeatureNameStatistics",
        "proto.featureStatistics.NumericStatistics",
        "proto.featureStatistics.StringStatistics",
        "proto.featureStatistics.CommonStatistics",
        "proto.featureStatistics.Histogram",
        "proto.featureStatistics.RankHistogram"
    ],
    path = "/facets-overview/common/test",
    deps = [
        ":externs",
        "//facets_overview/proto",
        "//facets_overview/common",
        "@org_tensorflow_tensorboard//tensorboard/components/tf_imports:web_component_tester",
    ],
    testonly = True
)

tensorboard_html_binary(
    name = "devserver",
    input_path = "/facets-overview/common/test/test.html",
    output_path = "/facets-overview/common/test/runner.html",
    deps = [":test"],
    testonly = True
)
