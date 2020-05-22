package(default_visibility = ["//visibility:public"])
load("@rules_proto//proto:defs.bzl", "proto_library")
load("@build_stack_rules_proto//java:java_proto_compile.bzl", "java_proto_compile")

alias(
    name = "protoc",
    actual = "@com_google_protobuf//:protoc",
)
alias(
  name = "protobuf",
  actual = "@com_google_protobuf//:protobuf",
)

proto_library(
    name = "repro_proto",
    srcs=["repro.proto"],
    deps = [])

java_proto_compile(
    name = "repro_java_proto",
    deps = [":repro_proto"])

java_library(name = "repro_java",
    srcs = [":repro_java_proto"])

