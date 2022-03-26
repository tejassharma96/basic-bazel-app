load("@build_bazel_rules_ios//rules:framework.bzl", "apple_framework")
load("@build_bazel_rules_ios//rules:app.bzl", "ios_application")
load("@build_bazel_rules_ios//rules:xcodeproj.bzl", "xcodeproj")

apple_framework(
    name = "UrlGet",
    srcs = glob(["UrlGet/*.h", "UrlGet/*.m", "UrlGet/*.swift"], exclude=["UrlGet/main.m"]),
    platforms = {"ios": "14.0"},
    visibility = ["//visibility:public"],
    deps = ["//Pods/SDWebImage:SDWebImage"]
)

ios_application(
    name = "ios-app",
    bundle_id = "Google.UrlGet",
    families = [
        "iphone",
        "ipad",
    ],
    srcs = ["UrlGet/main.m"],
    infoplists = [":UrlGet/UrlGet-Info.plist"],
    launch_storyboard = "UrlGet/UrlGetViewController.xib",
    minimum_os_version = "14.0",
    visibility = ["//visibility:public"],
    deps = [ ":UrlGet" ]
)

xcodeproj(
    name = "xcodeproj",
    bazel_path = "/opt/homebrew/bin/bazelisk",
    include_transitive_targets = True,
    generate_schemes_for_product_types = ["application"],
    infoplist_stub = "UrlGet/UrlGet-Info.plist",
    project_name = "ios-app",
    deps = [
        ":ios-app"
    ],
)