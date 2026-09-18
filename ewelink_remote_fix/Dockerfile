# Lokales Add-on: offizielles eWeLink-Remote-Gateway-Image, eine Zeile gepatcht (18.09.2026).
# Die Passivscan-Pruefung liest data_schema[0].description.suggested_value und verlangt `true`;
# HA >= 2025 liefert dort "passive" (Auswahlfeld mode). Upstream-Issue #80, ungeloest.
ARG BUILD_FROM=ghcr.io/ihost-open-source-project/hassio-ihost-ewelink-remote-amd64:0.3.1
FROM $BUILD_FROM
RUN sed -i "s#\['suggested_value'\])!==!!\[\])continue;#['suggested_value'])!==!![]\&\&String((_0x3d0094||{})['suggested_value'])!=='passive')continue;#" /app/server/src/ha.js \
 && grep -c "!=='passive')continue;" /app/server/src/ha.js
