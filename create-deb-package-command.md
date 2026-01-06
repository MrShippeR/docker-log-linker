# změnit verzi v názvu složky a v souboru /docker-log-linker/docker-log-linker-v*/DEBIAN/control
# zkompilovat balíček a přesunout do složky release
# poslední verzi dát do složky /release/latest/
dpkg-deb --build --root-owner-group ./docker-log-linker-v*
