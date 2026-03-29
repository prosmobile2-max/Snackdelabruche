# 🚀 Snack de la Bruche — Roadmap V3.0

> Ce document liste toutes les fonctionnalités avancées à développer après le menu QR statique.
> Stack recommandée : **Next.js 15 + TypeScript + Tailwind + Supabase + Better Auth**

---

## ✅ Phase 1 — DONE (Menu QR statique)
- [x] Design dark glassmorphism (#0F0F0F + rgba blur)
- [x] Header sticky avec statut "🟢 Ouvert · 15 min"
- [x] Mode "Petite faim / Grosse dalle" (filtre les plats)
- [x] Hero bento (promo midi + best-seller)
- [x] Navigation sticky smooth scroll par catégorie
- [x] Grille best-sellers avec photos + badges
- [x] Toutes catégories : Sandwichs, Tacos, Assiettes, Burgers, Extras, Desserts, Boissons, Bières
- [x] Bouton [+] sur chaque plat (préparatoire panier)
- [x] FAB WhatsApp + Appel en bas
- [x] Hébergé sur GitHub Pages (gratuit)

---

## 🟡 Phase 2 — Améliorations visuelles (1-2 jours)

### Photos manquantes
- [ ] Prendre les photos des plats : Tacos, Burgers, Assiettes, Desserts
- [ ] Intégrer les photos dans les sections correspondantes
- [ ] Optimiser les images (WebP, max 150Ko/image)

### UI/UX
- [ ] Remplacer bouton "Appeler" par le vrai numéro du snack
- [ ] Remplacer lien WhatsApp par le vrai numéro
- [ ] Logo SVG personnalisé (si le snack en a un)
- [ ] Micro-animations au scroll (fade-in des cartes)
- [ ] Descriptions marketing des plats (style "Triple viande saisie au grill...")
- [ ] QR code PNG téléchargeable (pour les tables)
- [ ] Page "À propos" (horaires, adresse, Google Maps)

---

## 🔴 Phase 3 — App de commande complète (Next.js)

> Nécessite un vrai projet web avec backend.
> Estimé : 3-4 semaines de développement.

### 🛒 Panier & Commande
- [ ] Panier persistant (localStorage ou Supabase)
- [ ] Barre flottante "🛒 Voir ma commande (2) — 24.80€"
- [ ] Page panier avec récap + modification quantités
- [ ] Suggestions upselling : "Ajouter des frites pour +2.50€ ?"
- [ ] Options personnalisation : sauce, supplément, taille

### 💳 Paiement
- [ ] Intégration Stripe (carte bancaire)
- [ ] Apple Pay / Google Pay One-Tap
- [ ] Reçu par email/SMS après commande

### 📲 Commande en cuisine
- [ ] Intégration API WhatsApp Business → notification en cuisine à chaque commande
- [ ] Dashboard cuisine (liste des commandes en cours, statuts)
- [ ] Interface tablet cuisine (Kanban : En attente → En préparation → Prêt)

### 📍 Real-Time Tracking
- [ ] Suivi commande en temps réel pour le client
- [ ] Statuts : `Commande reçue → En préparation 👨‍🍳 → Prêt à emporter ✅`
- [ ] Notification push quand prêt (PWA)

### 🎁 Fidélité
- [ ] Programme points : 1€ = 1 point
- [ ] QR code fidélité personnel par client
- [ ] Récompenses : -5% à partir de 100 points
- [ ] Historique commandes client

### 🤖 IA & Smart Features
- [ ] Suggestions combo intelligentes selon l'heure (midi vs soir)
- [ ] "Mode Petite faim / Grosse dalle" → réorganise le menu (déjà en Phase 1, à connecter au back)
- [ ] Plat du jour mis en avant automatiquement

---

## 🏗️ Stack technique recommandée

```
Frontend : Next.js 15 + TypeScript + Tailwind v3
Auth     : Better Auth (sessions client + dashboard admin)
DB       : Supabase (PostgreSQL + Storage photos)
Paiement : Stripe (webhooks)
Notifs   : WhatsApp Business API (Twilio ou 360dialog)
Deploy   : Vercel (gratuit jusqu'à un certain volume)
Push     : PWA Notifications (service worker)
```

---

## 💰 Estimation coûts mensuels (Phase 3)

| Service | Coût |
|---|---|
| Vercel (Pro si besoin) | 0-20€/mois |
| Supabase | 0-25€/mois |
| Stripe | 1.4% + 0.25€/transaction |
| WhatsApp Business API | ~50€/mois (volume moyen) |
| **Total estimé** | **~70-100€/mois** |

---

## 📌 Notes

- Le menu QR statique (Phase 1) est **suffisant pour démarrer** et coûte **0€/mois**
- La Phase 3 est pertinente si le snack veut **commander + payer depuis le téléphone**
- Conseil : commencer par les vraies photos (Phase 2) avant d'investir dans la Phase 3
