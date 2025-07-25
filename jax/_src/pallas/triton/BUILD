# Copyright 2023 The JAX Authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     https://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# Package for Triton-specific Pallas extensions

load(
    "//jaxlib:jax.bzl",
    "py_deps",
    "pytype_strict_library",
)

package(
    default_applicable_licenses = [],
    default_visibility = [
        "//jax:internal",
    ],
)

pytype_strict_library(
    name = "core",
    srcs = [
        "__init__.py",
        "core.py",
    ],
    deps = ["//jax/_src/pallas"],
)

pytype_strict_library(
    name = "primitives",
    srcs = ["primitives.py"],
    deps = [
        ":lowering",
        "//jax",
        "//jax:ad_util",
        "//jax:api_util",
        "//jax:core",
        "//jax:lax",
        "//jax:mlir",
        "//jax:partial_eval",
        "//jax:source_info_util",
        "//jax:util",
        "//jax/_src/lib",
        "//jax/_src/pallas",
    ] + py_deps("numpy"),
)

pytype_strict_library(
    name = "lowering",
    srcs = ["lowering.py"],
    deps = [
        "//jax",
        "//jax:ad_util",
        "//jax:api",
        "//jax:api_util",
        "//jax:config",
        "//jax:core",
        "//jax:custom_derivatives",
        "//jax:lax",
        "//jax:mlir",
        "//jax:partial_eval",
        "//jax:source_info_util",
        "//jax:state_types",
        "//jax:util",
        "//jax/_src/lib",
        "//jax/_src/pallas",
    ] + py_deps("numpy"),
)

pytype_strict_library(
    name = "pallas_call_registration",
    srcs = ["pallas_call_registration.py"],
    deps = [
        ":core",
        ":lowering",
        "//jax",
        "//jax:core",
        "//jax:frozen_dict",
        "//jax:mlir",
        "//jax/_src/lib",
        "//jax/_src/pallas",
    ],
)
