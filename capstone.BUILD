
package(default_visibility = ["//visibility:public"])

cc_library(
    name = "capstone",
    srcs = [
        "cs.c",
        "cs_priv.h",
        "LEB128.h",
        "MathExtras.h",
        "MCDisassembler.h",
        "MCFixedLenDisassembler.h",
        "MCInst.c",
        "MCInst.h",
        "MCInstrDesc.c",
        "MCInstrDesc.h",
        "MCRegisterInfo.c",
        "MCRegisterInfo.h",
        "SStream.c",
        "SStream.h",
        "utils.c",
        "utils.h",
    ] + glob([
        "arch/*/*.c",
        "arch/*/*.h",
        "arch/*/*.inc",
    ]),
    hdrs = [":capstone-headers"],
    includes = ["include"],
    copts = [
        "-w",
        "-DCAPSTONE_HAS_ARM",
        "-DCAPSTONE_HAS_ARM64",
        "-DCAPSTONE_HAS_BPF",
        "-DCAPSTONE_HAS_EVM",
        "-DCAPSTONE_HAS_M680X",
        "-DCAPSTONE_HAS_M68K",
        "-DCAPSTONE_HAS_MIPS",
        "-DCAPSTONE_HAS_MOS65XX",
        "-DCAPSTONE_HAS_POWERPC",
        "-DCAPSTONE_HAS_RISCV",
        "-DCAPSTONE_HAS_SPARC",
        "-DCAPSTONE_HAS_SYSZ",
        "-DCAPSTONE_HAS_TMS320C64X",
        "-DCAPSTONE_HAS_WASM",
        "-DCAPSTONE_HAS_X86",
        "-DCAPSTONE_HAS_XCORE",
        "-DCAPSTONE_USE_SYS_DYN_MEM",
    ],
)

filegroup(
    name = "capstone-headers",
    srcs = glob(["include/capstone/*.h"]),
)
