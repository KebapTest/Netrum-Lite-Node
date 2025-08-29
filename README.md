# Netrum Lite Node — Hızlı Kurulum (Ubuntu)

Aşağıdaki adımlar **yalın** kurulum ve kullanım içindir.

---

## 0) Tek satır kurulum

```bash
sudo bash -lc 'apt update && apt install -y curl bc jq speedtest-cli git ca-certificates lsb-release build-essential python3 && curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && apt remove -y libnode-dev 2>/dev/null || true; apt install -y nodejs && cd /root && if [ -d netrum-lite-node/.git ]; then cd netrum-lite-node && git reset --hard && git pull --ff-only; else git clone https://github.com/NetrumLabs/netrum-lite-node.git && cd netrum-lite-node; fi && rm -rf node_modules package-lock.json && npm install && npm link --force && (netrum --version || netrum | head -n 5)'
```

---

## 1) Cüzdan

```bash
cd ~/netrum-lite-node
netrum-new-wallet      # ya da: netrum-import-wallet
```

## 2) .base adı (tarayıcıda mintle → sonra kontrol et) https://www.base.org/names

```bash
netrum-check-basename
netrum-node-id
```

## 3) Kayıt (on-chain)

```bash
netrum-node-register
```

## 4) Sync

```bash
netrum-sync
netrum-sync-log
```

## 5) Mining

```bash
netrum-mining
netrum-mining-log
```

## 6) Claim (24 saat sonra)

```bash
netrum-claim
```

## 7) Güncelleme (kısa)

```bash
cd ~/netrum-lite-node && git pull && npm install && npm link --force
```

## 8) Hızlı kontroller (opsiyonel)

```bash
netrum-system
netrum-wallet
sudo systemctl status netrum-node.service
netrum-sync-log
netrum-mining-log
```
