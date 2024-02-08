workspace(name = "com_chengtan9907_openstl")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

RULES_PYTHON_SHA="d71d2c67e0bce986e1c5a7731b4693226867c45bfe0b7c5e0067228a536fc580"
RULES_PYTHON_VERSION="0.29.0"

http_archive(
    name = "rules_python",
    sha256 = RULES_PYTHON_SHA,
    strip_prefix = "rules_python-{}".format(RULES_PYTHON_VERSION),
    url = "https://github.com/bazelbuild/rules_python/releases/download/{}/rules_python-{}.tar.gz".format(RULES_PYTHON_VERSION,RULES_PYTHON_VERSION),
)

load("@rules_python//python:repositories.bzl", "py_repositories")

py_repositories()

load("@rules_python//python:repositories.bzl", "python_register_toolchains")

python_register_toolchains(
    name = "python_310",
    python_version = "3.10.13",
)

load("@python_310//:defs.bzl", "interpreter")
load("@rules_python//python:pip.bzl", "pip_parse")

pip_parse(
    name = "pip_deps",
    enable_implicit_namespace_pkgs = True,
    python_interpreter_target = interpreter,
    requirements_lock = "//:requirements_lock.txt",
)

load("@pip_deps//:requirements.bzl", install_pip_deps = "install_deps")

install_pip_deps()
