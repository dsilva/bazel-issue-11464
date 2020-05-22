workspace(name = "repro")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

protobuf_version = "3.12.1"
http_archive(
    name = "com_google_protobuf",
    strip_prefix = "protobuf-" + protobuf_version,
    urls = ["https://github.com/google/protobuf/archive/v%s.zip" % protobuf_version],
)

BAZELBUILD_RULES_PROTO_COMMIT = "8b81c3ccfdd0e915e46ffa888d3cdb6116db6fa5"
http_archive(
    name = "rules_proto",
    strip_prefix = "rules_proto-" + BAZELBUILD_RULES_PROTO_COMMIT,
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_proto/archive/%s.tar.gz" % BAZELBUILD_RULES_PROTO_COMMIT,
        "https://github.com/bazelbuild/rules_proto/archive/%s.tar.gz" % BAZELBUILD_RULES_PROTO_COMMIT,
    ],
)
load("@rules_proto//proto:repositories.bzl", "rules_proto_dependencies", "rules_proto_toolchains")
rules_proto_dependencies()
rules_proto_toolchains()

STACKB_RULES_PROTO_COMMIT = "0a888dbeacebfe06acb7ba740e0723b1adb0dd52"
STACKB_RULES_PROTO_SHA = "966316838b6454ca2f51718d6a801f8ebf7d1d41c82a51ac24af4d92115fa323"
http_archive(
    name = "build_stack_rules_proto",
        urls = ["https://github.com/stackb/rules_proto/archive/%s.tar.gz" % STACKB_RULES_PROTO_COMMIT],
    sha256 = STACKB_RULES_PROTO_SHA,
    strip_prefix = "rules_proto-%s" % STACKB_RULES_PROTO_COMMIT,
)
load("@build_stack_rules_proto//java:deps.bzl", "java_proto_compile")
java_proto_compile()

bazel_toolchains_commit = "3.1.0"
http_archive(
    name = "bazel_toolchains",
    strip_prefix = "bazel-toolchains-" + bazel_toolchains_commit,
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/bazel-toolchains/archive/%s.tar.gz" % bazel_toolchains_commit,
        "https://github.com/bazelbuild/bazel-toolchains/archive/%s.tar.gz" % bazel_toolchains_commit,
    ],
)
load("@bazel_toolchains//rules:rbe_repo.bzl", "rbe_autoconfig")
rbe_autoconfig(name = "rbe_default")

