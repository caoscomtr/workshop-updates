# Guncelleme kanali — v0.11

Bu klasoru `python build/kur.py --release-url ...` uretti; **elle duzenleme yok**.

## Yuklenecek iki dosya
1. `Workshop_v0.11_update.zip`  (42.1 MB, 475 dosya) — adresi: `https://github.com/caoscomtr/workshop-updates/releases/download/v0.11/Workshop_v0.11_update.zip`
2. `surum.json` (bu klasorde) — istemcinin okudugu dosya.

Ikisi de yukaridaki adresle AYNI klasorde yayinlanmali; istemci once
`surum.json`u okur, sonra `paket` alanindaki adresi indirir ve sha256'yi
dogrular (`sha256=d39666b488ac9cc333dc0d830b3fb6e9e8f778e10d85ea0567bdbe5de267e7dc`). Sha tutmazsa kurulum YAPILMAZ.

## Istemcinin baktigi adres
`src/guncelle.py` -> `GUNCELLEME_URL` (surum.json'un TAM adresi olmali).

## Delta
`delta=False`, `taban_surum=None`. Delta paket yalniz tabandan bu yana
degisen dosyalari tasir; tabandan ESKI kurulumlar Nexus'taki tam pakete
yonlendirilir (istemci kendisi soyler). Nexus'a yeni TAM paket yuklerken
`--taban-sifirla` ile tabani o surume tasi.
