# Native Scarlet

The `scarlet` branch tracks the native AArch64 port. Its pthread discovery
uses immediate, global symbol binding, matching the Scarlet loader ABI.
The upstream source license and notices remain in place.

Build `libGLdispatch` and `libOpenGL` with pthread TSD, ELF TLS disabled,
entrypoint patching disabled, and the portable C dispatch stubs. X11, GLX,
EGL and GLES are outside this configuration. The matching native SDK companion
and compiler builtins provide the C import closure. Use installed libraries;
Meson's build-tree RPATH is not accepted by the native loader.

This is a vendor-neutral dispatch loader. It does not supply a window-system
integration or an OpenGL rendering vendor. Applications still need a real
current OpenGL context before creating capabilities or rendering. Native
acceptance loads the provider and verifies rejection of a contextless
capability query.
