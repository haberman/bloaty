workspace(name = "bloaty")

load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

git_repository(
    name = "com_google_absl",
    commit = "df3ea785d8c30a9503321a3d35ee7d35808f190d",  # LTS 2020-02-25
    remote = "https://github.com/abseil/abseil-cpp.git",
    shallow_since = "1583355457 -0500",
)

git_repository(
    name = "com_google_protobuf",
    remote = "https://github.com/protocolbuffers/protobuf.git",
    commit = "c8f76331abf682c289fa79f05b2ee39cc7bf5a48",  # Need to use Git until proto3 optional is released
)

http_archive(
     name = "com_google_googletest",
     urls = ["https://github.com/google/googletest/archive/b6cd405286ed8635ece71c72f118e659f4ade3fb.zip"],  # 2019-01-07
     strip_prefix = "googletest-b6cd405286ed8635ece71c72f118e659f4ade3fb",
     sha256 = "ff7a82736e158c077e76188232eac77913a15dac0b22508c390ab3f88e6d6d86",
)
