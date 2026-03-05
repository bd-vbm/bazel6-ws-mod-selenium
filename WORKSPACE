
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# --- rules_jvm_external (Maven/Selenium) ---
RULES_JVM_EXTERNAL_TAG = "6.6"
RULES_JVM_EXTERNAL_SHA = "3afe5195069bd379373528899c03a3072f568d33bd96fe037bd43b1f590535e7"

http_archive(
    name = "rules_jvm_external",
    strip_prefix = "rules_jvm_external-%s" % RULES_JVM_EXTERNAL_TAG,
    sha256 = RULES_JVM_EXTERNAL_SHA,
    urls = [
        "https://github.com/bazel-contrib/rules_jvm_external/releases/download/%s/rules_jvm_external-%s.tar.gz"
        % (RULES_JVM_EXTERNAL_TAG, RULES_JVM_EXTERNAL_TAG),
    ],
)

load("@rules_jvm_external//:repositories.bzl", "rules_jvm_external_deps")
rules_jvm_external_deps()
load("@rules_jvm_external//:setup.bzl", "rules_jvm_external_setup")
rules_jvm_external_setup()
load("@rules_jvm_external//:defs.bzl", "maven_install")

maven_install(
    name = "maven",
    artifacts = [
        "org.seleniumhq.selenium:selenium-java:4.18.0",
        "org.testng:testng:7.12.0",
    ],
    repositories = ["https://repo1.maven.org/maven2"],
    # To pin, generate a lock file and set:
    # maven_install_json = "@//:maven_install.json",
)

# --- rules_haskell v1.0 ---
http_archive(
    name = "rules_haskell",
    sha256 = "4cae22bc84f327bf3cb7605021c3663160ff6bc8a0b7b6266062366bcbd19e79",
    strip_prefix = "rules_haskell-1.0",
    urls = ["https://github.com/tweag/rules_haskell/releases/download/v1.0/rules_haskell-1.0.tar.gz"],
)

load("@rules_haskell//haskell:repositories.bzl", "rules_haskell_dependencies")
rules_haskell_dependencies()

load("@rules_haskell//haskell:toolchain.bzl", "rules_haskell_toolchains")
rules_haskell_toolchains(
    version = "9.6.5",
)
