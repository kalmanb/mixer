package(default_visibility = ["//tools/codegen/pkg/interfacegen:__pkg__"])

load("@org_pubref_rules_protobuf//protobuf:rules.bzl", "proto_compile")
load("//tools/codegen:generate.bzl", "mixer_proto_library")

mixer_proto_library(
    name = "list_template_library",
    testonly = True,
    protos = ["ListTemplate.proto"],
)

mixer_proto_library(
    name = "log_template_library",
    testonly = True,
    protos = ["LogTemplate.proto"],
)

mixer_proto_library(
    name = "metric_template_library",
    testonly = True,
    protos = ["MetricTemplate.proto"],
)

mixer_proto_library(
    name = "quota_template_library",
    testonly = True,
    protos = ["QuotaTemplate.proto"],
)

filegroup(
    name = "descriptors",
    testonly = True,
    srcs = [
        "list_template_library_proto.descriptor_set",
        "log_template_library_proto.descriptor_set",
        "metric_template_library_proto.descriptor_set",
        "quota_template_library_proto.descriptor_set",
    ],
)

filegroup(
    name = "generated_files",
    testonly = True,
    srcs = [
        "list_template_library_processor.gen.go",
        "list_template_library_tmpl.proto",
        "log_template_library_processor.gen.go",
        "log_template_library_tmpl.proto",
        "metric_template_library_processor.gen.go",
        "metric_template_library_tmpl.proto",
        "quota_template_library_processor.gen.go",
        "quota_template_library_tmpl.proto",
    ],
)

filegroup(
    name = "golden_files",
    testonly = True,
    srcs = [
        "ListTemplateGenerated.golden.proto",
        "ListTemplateProcessorInterface.golden.go",
        "LogTemplateGenerated.golden.proto",
        "LogTemplateProcessorInterface.golden.go",
        "MetricTemplateGenerated.golden.proto",
        "MetricTemplateProcessorInterface.golden.go",
        "QuotaTemplateGenerated.golden.proto",
        "QuotaTemplateProcessorInterface.golden.go",
    ],
)

proto_compile(
    name = "error_template",
    testonly = True,
    args = [
        "--include_imports",
        "--include_source_info",
    ],
    imports = [
        "external/com_github_google_protobuf/src",
    ],
    inputs = [
        "//pkg/adapter/template:protos",
        "@com_github_google_protobuf//:well_known_protos",
    ],
    protos = ["ErrorTemplate.proto"],
)

filegroup(
    name = "error_test_files",
    testonly = True,
    srcs = [
        "ErrorTemplate.baseline",
        "error_template.descriptor_set",
    ],
)