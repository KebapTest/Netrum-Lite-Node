# Netrum Lite Node — Hızlı Kurulum (Ubuntu)

Kayıt esnasında cüzdanınızda 0.0002 - 0.0005 BASE olması gerekmektedir.

---

## Donanım ve Ağ Gereksinimleri

Netrum Lite Node’un stabil çalışması için en az aşağıdaki gereksinimleri karşılayın.

### Donanım (Hardware)
| Bileşen   | Minimum | Önerilen |
|----------|---------|----------|
| CPU      | 2 Çekirdek | 2+ Çekirdek |
| RAM      | 4 GB    | 6 GB veya üzeri |
| Disk     | 50 GB SSD | 100 GB SSD |

> **Not:** SSD depolama performans ve stabilite için **şiddetle önerilir**.

### Ağ (Network)
| Tür       | Minimum Hız |
|----------|--------------|
| Download | 10 Mbps      |
| Upload   | 10 Mbps      |

---

## 0) Tek satır kurulum

```bash
sudo bash -lc 'apt update && apt install -y curl bc jq speedtest-cli git ca-certificates lsb-release build-essential python3 && curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && apt remove -y libnode-dev 2>/dev/null || true; apt install -y nodejs && cd /root && if [ -d netrum-lite-node/.git ]; then cd netrum-lite-node && git reset --hard && git pull --ff-only; else git clone https://github.com/NetrumLabs/netrum-lite-node.git && cd netrum-lite-node; fi && rm -rf node_modules package-lock.json && npm install && npm link --force && (netrum --version || netrum | head -n 5)'
```

---

## 1) Cüzdan

```bash
cd ~/netrum-lite-node
netrum-new-wallet      # cüzdanınız varsa : netrum-import-wallet
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

## 6) Claim (24 saat sonra) claim her defasında 0.00002 - 0.00003 BASE tutar.  

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
