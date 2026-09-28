
# SASS CONSEIL IA - sass-conseil-ia - Firebase Backend Complet

## Projet Firebase existant: sass-conseil-ia
IBAN Nickel: FR7616598000010826488000135
Tel: 06 05 69 15 55
Verify Token WhatsApp: SASS2024TROYES
Webhook: https://us-central1-sass-conseil-ia.cloudfunctions.net/whatsappWebhook

## STRUCTURE
- Firestore: clients, devis, logs, abonnements, users
- Auth: Email/password
- Functions:
  1. whatsappWebhook (GET challenge, POST messages)
  2. stripeWebhook (paiements -> Nickel J+2)
  3. autonomousEngine (toutes les 5 min)
  4. createPaymentLink (Stripe Checkout -> Nickel)
  5. initSassData (20 fiches Troyes réels)
  6. createSubscription (MRR 199/299/499)
- Hosting: public/index.html avec Auth + Firestore temps réel

## SETUP DEPUIS TELEPHONE (Firebase Studio ou Console)

1. Va sur console.firebase.google.com > projet sass-conseil-ia
2. Authentication > Méthode de connexion > Email/Mot de passe > Activer
3. Firestore Database > Créer base > Mode test > europe-west
4. Functions > Configurer: 
   firebase functions:config:set whatsapp.token="EAA..." whatsapp.phone_id="123..." stripe.secret="sk_live_..." stripe.webhook="whsec_..." 
   Ou dans Console > Functions > Variables d'environnement: STRIPE_SECRET_KEY, STRIPE_WEBHOOK_SECRET, WHATSAPP_TOKEN, WHATSAPP_PHONE_ID
5. Hosting > Déployer

## DEPLOIEMENT (depuis Firebase Studio sur mobile)
firebase login
firebase use sass-conseil-ia
firebase deploy --only firestore:rules,functions,hosting

## APRES DEPLOIEMENT
- URL Webhook WhatsApp à mettre dans developers.facebook.com: https://us-central1-sass-conseil-ia.cloudfunctions.net/whatsappWebhook
- Verify token: SASS2024TROYES
- Dans public/index.html: remplace firebaseConfig par ta vraie config (Paramètres projet > Tes applications > SDK)

## 20 FICHES CLIENTS TROYES
Boulangerie Faye, Gérard, Banette, Courtalon, El Majless, Rosafa, Jardin, Roma, Coiffeurs, Garages, etc - tous réels Troyes 10000

## APP WEB
https://sass-conseil-ia.web.app - connexion Email/mdp - dashboard CA/MRR/Logs temps réel
