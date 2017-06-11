# Vita LuaJIT

This is a vitasdk port of LuaJIT with JIT and FFI support.
LuaJIT is a Just-In-Time (JIT) compiler for the Lua programming language.
See original REAMDE.orig for details.

## Build deps

You can install build dependencies with [vdpm](https://github.com/vitasdk/vdpm). [vita-libdl](https://github.com/hyln9/vita-libdl) is required for FFI support.

## Build LuaJIT

```
# the following steps will generate a static library libluajit.a
cd src
make HOST_CC="gcc -m32" CROSS=arm-vita-eabi- TARGET_SYS=PSP2 TARGET_FLAGS="-marm -fno-optimize-sibling-calls" PREFIX="ux0:/data/luajit"
```

## Link LuaJIT

When linking with LuaJIT, don't forget to adjust `LUA_LROOT` of `luaconf.h` according to `PREFIX` defined above.
If LuaJIT is built with FFI support, `vita-libdl` must be initialized via `dlinit` and `dldbadd` before calling any LuaJIT API.
