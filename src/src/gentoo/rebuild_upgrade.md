## Upgrading the system
- Rebuild all the packages & Update the system's `@world` set: `emerge -qeuvNDU --jobs="$(nproc)" --with-bdeps=y --keep-going @world`.