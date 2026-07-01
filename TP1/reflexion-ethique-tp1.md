# Reflexion ethique, legale et RGPD - TP1 Ollama/Continue.dev
## Informations
- Nom : Alexis LOBO, Nathan VILLAIN et Quentin CABRERA
- Date : 01/07/2026
## 1. Analyse des scenarios
 
### Scenario 1 : Confidentialite des donnees
 
**Analyse :**
 
L'utilisation d'Ollama en local limite l'envoi de donnees vers un service tiers, ce qui constitue un avantage important pour la confidentialite. Cependant, cela ne signifie pas que tous les risques disparaissent : les prompts peuvent contenir des donnees personnelles, les fichiers locaux peuvent etre accessibles par d'autres utilisateurs de la machine, et les journaux ou historiques doivent etre maitrises.
 
Dans un contexte professionnel, il faut eviter d'inserer des donnees reelles de clients dans les prompts. La bonne pratique consiste a anonymiser ou synthetiser les donnees avant de les utiliser, meme avec un outil local.
 
**Principes RGPD concernes :**
 
- Minimisation des donnees
- Limitation des finalites
- Integrite et confidentialite
- Limitation de la conservation
- Transparence
 
**Risques identifies :**
 
- Inclusion de donnees personnelles dans les prompts
- Conservation locale non documentee
- Acces non autorise au poste de developpement
- Confusion entre environnement local et outil cloud
 
**Mesures d'attenuation :**
 
- Utiliser des donnees anonymisees ou fictives
- Restreindre Ollama a `localhost`
- Chiffrer le disque
- Documenter les usages IA dans une charte interne
- Ne jamais placer de secrets, tokens ou mots de passe dans les prompts
 
### Scenario 2 : Propriete intellectuelle
 
**Analyse :**
 
Le code genere par IA doit etre relu comme tout code produit dans un projet professionnel. Meme si le modele est execute localement, il peut produire du code proche d'exemples publics ou incompatible avec certaines exigences de licence. La responsabilite finale revient a l'equipe qui integre le code dans le projet.
 
Avant un usage commercial, il faut verifier la licence du modele utilise et la politique de l'organisation concernant les sorties d'IA. La tracabilite est aussi utile : conserver le prompt, le modele utilise et la date peut aider en cas d'audit.
 
**Principes et points juridiques concernes :**
 
- Licence du modele
- Conditions d'usage commercial
- Droit d'auteur sur les sorties generees
- Politique interne de l'entreprise
 
**Risques identifies :**
 
- Reutilisation d'un extrait trop proche d'un code existant
- Licence du modele incompatible avec l'usage prevu
- Absence de tracabilite
 
**Mesures d'attenuation :**
 
- Verifier les licences des modeles
- Relire et tester tout code genere
- Documenter les prompts importants
- Eviter d'accepter du code complexe sans comprehension
 
### Scenario 3 : Biais algorithmiques
 
**Analyse :**
 
Les modeles peuvent reproduire des biais presents dans leurs donnees d'entrainement. Dans le code, cela peut se manifester par des exemples stereotypes, des noms de variables non neutres, des hypotheses culturelles ou des jeux de donnees de test peu representatifs.
 
Le developpeur reste responsable de la validation finale. Il doit detecter ces biais, les corriger et enrichir les tests avec des cas limites et des situations variees.
 
**Risques identifies :**
 
- Variables ou exemples stereotypes
- Documentation non inclusive
- Tests incomplets
- Reproduction de pratiques obsoletes
 
**Mesures d'attenuation :**
 
- Relire les noms, exemples et commentaires
- Tester avec des donnees variees
- Signaler les comportements problematiques aux projets concernes
- Sensibiliser l'equipe aux biais algorithmiques
 
### Scenario 4 : Transparence et tracabilite
 
**Analyse :**
 
Si Continue.dev est impose dans une organisation, les developpeurs doivent etre informes de ce que l'outil analyse, de la configuration utilisee et des limites d'usage. Meme localement, l'analyse du code par un outil IA doit etre expliquee clairement.
 
La tracabilite permet de savoir quand l'IA a ete utilisee, quel modele a genere une proposition et quelle revue humaine a ete effectuee. Cela ne doit pas devenir une surveillance excessive, mais un mecanisme de qualite et de conformite.
 
**Risques identifies :**
 
- Manque d'information des developpeurs
- Absence de politique claire
- Difficulte a auditer le code genere
- Responsabilites mal definies
 
**Mesures d'attenuation :**
 
- Rediger une charte d'utilisation IA
- Documenter les prompts importants
- Indiquer les parties significatives generees par IA si necessaire
- Prevoir une revue humaine obligatoire
 
## 2. Principes RGPD et leur application
 
| Principe RGPD | Application a Ollama/Continue | Conformite actuelle | Actions necessaires |
|---------------|-------------------------------|---------------------|---------------------|
| Liceite, loyaute, transparence | Informer les utilisateurs de l'usage d'IA | Partielle | Rediger une charte |
| Limitation des finalites | Utiliser l'IA seulement pour l'aide au developpement | A verifier | Definir les cas autorises |
| Minimisation des donnees | Eviter les donnees personnelles dans les prompts | A renforcer | Anonymiser les donnees |
| Exactitude | Verifier les sorties du modele | Partielle | Tests et revue humaine |
| Limitation de la conservation | Controler prompts, logs et historiques | A verifier | Definir une duree de retention |
| Integrite et confidentialite | Garder le traitement en local et securiser le poste | Bonne base | Chiffrement, acces restreint |
 
## 3. Recommandations concretes pour usage ethique
 
### Avant d'utiliser l'IA
 
1. Verifier que les donnees utilisees ne sont pas sensibles.
2. Choisir un modele compatible avec l'usage prevu.
3. Lire les licences des modeles.
4. Definir les limites d'utilisation dans une charte.
 
### Pendant l'utilisation
 
1. Ne pas copier de secrets ou de donnees clients dans les prompts.
2. Demander des explications en plus du code.
3. Comparer plusieurs propositions si la tache est critique.
4. Garder une trace des prompts importants.
 
### Apres generation de code
 
1. Relire le code ligne par ligne.
2. Executer les tests.
3. Verifier la securite et les performances.
4. Documenter les modifications significatives.
 
### En cas de doute
 
1. Ne pas integrer le code sans revue humaine.
2. Demander un avis a un referent technique ou juridique.
3. Remplacer les donnees reelles par des donnees fictives.
4. Supprimer les prompts ou traces inutiles.
 
## 4. Checklist de conformite pour utilisation d'IA locale
 
### Configuration technique
 
- [ ] Ollama installe en local
- [ ] Continue.dev configure pour utiliser uniquement des modeles locaux
- [ ] Pas de telemetrie activee ou telemetrie documentee
- [ ] Logs securises et localises
- [ ] Acces au serveur Ollama restreint a localhost
 
### Donnees et confidentialite
 
- [ ] Pas de donnees personnelles reelles dans les prompts
- [ ] Donnees sensibles anonymisees avant utilisation
- [ ] Politique de retention des conversations definie
- [ ] Procedure de suppression documentee
- [ ] Chiffrement du disque active
 
### Propriete intellectuelle
 
- [ ] Licences des modeles verifiees
- [ ] Code genere revise par un humain
- [ ] Attribution documentee si necessaire
- [ ] Usage commercial clarifie
- [ ] Verification anti-plagiat effectuee si besoin
 
### Biais et equite
 
- [ ] Revue critique des exemples generes
- [ ] Tests sur cas limites
- [ ] Commentaires et noms de variables inclusifs
- [ ] Procedure de signalement des biais
 
### Transparence et tracabilite
 
- [ ] Developpeurs informes de l'usage d'IA
- [ ] Prompts importants documentes
- [ ] Code genere identifiable si necessaire
- [ ] Registre RGPD mis a jour si applicable
 
### Securite
 
- [ ] Continue.dev a jour
- [ ] Ollama a jour
- [ ] Scan du code genere
- [ ] Aucun secret dans les prompts
- [ ] Environnement de developpement securise
 
### Responsabilite
 
- [ ] Responsable identifie pour l'usage IA
- [ ] Procedure d'escalade definie
- [ ] Plan de gestion des incidents
- [ ] Audit regulier des pratiques
 
## 5. Reflexion personnelle
 
### Ce que j'ai appris
 
[A personnaliser : expliquez ce que vous avez compris sur l'IA locale, la confidentialite, les limites techniques et la responsabilite humaine.]
 
### Mes inquietudes
 
[A personnaliser : donnees sensibles, confiance excessive dans le code genere, licences, biais, securite.]
 
### Mes engagements
 
[A personnaliser : relire le code, tester, ne pas envoyer de donnees sensibles, documenter les usages.]
 
## 6. Comparaison Local vs Cloud
 
| Critere | Ollama local | ChatGPT/Claude cloud |
|---------|--------------|----------------------|
| Confidentialite | Donnees traitees sur la machine | Donnees transmises a un fournisseur |
| RGPD | Plus simple si aucune donnee ne sort | Necessite analyse du sous-traitant et transferts |
| Propriete intellectuelle | Depend de la licence du modele local | Depend des conditions du fournisseur |
| Tracabilite | A organiser localement | Souvent fournie partiellement par la plateforme |
| Responsabilite | Forte responsabilite de l'utilisateur | Responsabilite partagee avec le fournisseur |
| Cout de conformite | Configuration interne a maitriser | Contrats, DPA et politiques fournisseur a verifier |
 
## 7. Conclusion
 
L'IA locale peut etre plus favorable a la confidentialite qu'une solution cloud, mais elle n'est pas automatiquement plus ethique. Elle devient pertinente si elle est accompagnee de bonnes pratiques : minimisation des donnees, securisation du poste, verification des licences, revue humaine du code et documentation claire des usages.