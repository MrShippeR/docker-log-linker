# změnit verzi v názvu složky a v souboru /docker-log-linker/docker-log-linker-v*/DEBIAN/control
# zkompilovat balíček a přesunout do složky release
dpkg-deb --build --root-owner-group ./docker-log-linker-v*
