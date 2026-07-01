# TP1 : Installation et configuration IA locale
 
Nom prenom : Alexis LOBO, Nathan VILLAIN et Quentin CABRERA
 
Date : 01/07/2026
 
## Sommaire
 
- Partie 2 : Installation d'Ollama
- Partie 3 : Telechargement et gestion des modeles
- Partie 4 : API Ollama
- Partie 5 : Installation de Continue.dev
- Partie 6 : Utilisation pratique
- Partie 7 : Bonnes pratiques
- Partie 8 : Reflexion ethique, legale et RGPD
 
## Partie 2 : Installation d'Ollama

- Installation d'Ollama :  
![Installation d'Ollama](img/install.png)

- Version d'Ollama :  
![Version d'Ollama](img/ollama_installation.png)

- Liste des modeles :  
![Liste modeles](img/ollama_models.png)

## Partie 3 : Telechargement et gestion des modeles

- Installation des 3 modeles :  
![3 modeles](img/install.png)

### Voici des tests comparatif :

1. Llama :  
![premier modele](img/ollama_test_llama.png)

2. Codellama :  
![deuxième modele](img/ollama_test_codellama.png)

3. Mistral :  
![troisieme modeles](img/ollama_test_mistral.png)

## Tableau de synthese
 
| Critere | Llama 3.2 3B | CodeLlama 7B | Mistral 7B |
|---------|--------------|--------------|------------|
| Exactitude | 4/5 | 4/5 | 4/5 |
| Style | 4/5 | 3/5 | 4/5 |
| Documentation | 4/5 | 4/5 | 4/5 |
| Type hints | 3/5 | 3/5 | 4/5 |
| Pertinence | 4/5 | 4/5 | 4/5 |
| Vitesse | 4/5 | 3/5 | 3/5 |
| Total | 23/30 | 21/30 | 23/30 |

#### Exemple de sortie avec la commande show :    
![commande show](img/test_command_show.png)

### Personnalisation d'un modele : 

Pour la personnalisation d'un modele nous devons passer par un ModelFile et voici celui que nous avons utiliser :  
![modelfile](img/contenu_modelfile.png)
(le modelfile se trouve dans le depot GIT si besoin dans le dossier "Fichiers" )

Puis voici la creation du modele :  
![creation modelefile](img/create_modelfile.png)

Voici un exemple de réponse provenant du custom llama :  
![reponse custom llama](img/test_custom_model_modelfile.png)

### Comparaison du meme modele avec differentes quantizations

Dans ce test nous avons pris le modele llama en quantization Q4 et Q8.  
Installation du modeles en différents quantization :  
![install model dif. quantization](img/install_2modeles_dif.png)

#### Voici maintenant les test réaliser sur les modeles : 
- Modele Q4 :
![Q4](img/test_llamaQ4.png)

- Modele Q8 :
![Q8](img/test_llamaQ8.png)

Il existe plusieurs versions d'un même modèle afin de s'adapter aux différentes contraintes matérielles et aux besoins des utilisateurs. Les versions les plus légères (comme Q4_K_M) occupent moins d'espace disque, consomment moins de mémoire RAM et sont plus rapides à exécuter. Les versions plus précises (comme Q8_0) sont plus volumineuses et demandent davantage de ressources, mais elles peuvent produire des réponses légèrement plus précises sur des tâches complexes.

Nous avons eu l’occasion de créer grâce a un Modelfile un agent de revue de code.
Voici le modelfile :
![Contenue Code Reviewer](img/contenu_codereviewer_modelfile.png)

Puis la creation du modele :
![Creation Code Reviewer](img/create_codereviewer_modelfile.png)

Et voici le test du CodeReviewer : 
![Test Code Reviewer](img/test_codereviewer_modelfile.png)

## Partie 4 : API Ollama

Nous avons eu l'occasion d'utiliser l'API de Ollama, cette API nous a permis d'interagir avec les modeles sans passer par le CLI.

Voici un test de cette API avec une réponse non-formater :  
![API non-formater](img/api_test_non-formater.png)

Puis on a pu modifier la requette API pour faire en sorte que la réponse soit formater, voici un exemple :  
![API formater](img/api_test_formater.png)
Pour avoir se résultat nous avons du désactiver le stream dans le body de la requete API.  

Nous avons tester aussi le mode conversationnel :
![code deterministe](img/api_test_2.png)

Voici le test que était demander dans le TP1 avec l'utilisaton de POSTMAN :
![API Postman](img/api_test_postmane.png)

Nous avons pu effectuer un exemple de generation de code deterministe, et en lancant 3 fois la commande j'avais obtenue exactement le meme code.

## Partie 5 : Installation de Continue.dev

Continue.dev permet d'utiliser les modeles locaux directement dans l'IDE. L'interet principal est de beneficier d'un assistant de developpement sans sortir de VS Code et sans envoyer automatiquement le code vers un service distant.
 
Pour l'installer, il faut aller dans VSCode > Extensions et chercher "Continue - open-source AI code agent"
![Continue install VSCODE](img/continue_install_vscode.png)
 
Nous avons du télécharger le modele d'embeddings via cette commande :
```
ollama pull nomic-embed-text
```
 
Ensuite, nous avons du configurer le fichier config.json comme présenté sur la capture d'écran :
![Config.json](img/continue_config.png)
 
 
 
Après, nous avons testé Continue pour vérifier son fonctionnement directement en chattant avec lui :
![test continue](img/continue_chat.png)
 
## Partie 6 : Utilisation pratique

Nous avons voulu testé Continue sur du codage spécifique et voici le résultat:
![Test Script](img/partie6_code_spe.png)
 
Nous avons voulu testé sur de la création d'API donc voila la discussion et le résultat :
![création d'API](img/partie6_fastAPI.png)

![résultat d'API](img/partie6_resultat.png)
 
Et nous avons voulu testé l'autocompletion intelligente :
![autocompletion intelligente](img/continue_autocomplete.png)

## Partie 7 : Bonnes pratiques

### Rédiger de bons prompts
 
Pour obtenir un bon résultat avec une IA de code, il faut donner des consignes précises. Un bon prompt doit indiquer le contexte du projet, le langage utilisé, le framework, les contraintes techniques et le résultat attendu.
 
La méthode **CLEAR** permet de structurer un prompt :
 
- **Contexte** : expliquer le problème et l’objectif.
- **Langage** : préciser le langage, le framework et les versions.
- **Exemples** : donner des exemples d’entrée et de sortie.
- **Attentes** : préciser le style de code, les conventions et les contraintes.
- **Résultats** : décrire clairement ce que l’on veut obtenir.
 
### Exemple de bon prompt
 
```text
Contexte : Je développe une API e-commerce en Python avec FastAPI.
Tâche : Crée une fonction de recherche de produits.
Contraintes : type hints, docstring, gestion des erreurs, SQLAlchemy.
Résultat attendu : une liste de produits triés par pertinence.
Exemple : search_products("ordinateur portable", max_price=1000)
```
 
### Limites à connaître
 
L’IA peut produire du code incorrect ou inventer des fonctions qui n’existent pas. Il faut donc toujours tester le code généré et vérifier la documentation officielle.
 
Elle peut aussi oublier une partie du contexte si on lui donne trop d’informations. Il vaut mieux fournir uniquement les fichiers ou extraits nécessaires.
 
Enfin, l’IA peut proposer du code obsolète ou non sécurisé. Le développeur doit relire le code, lancer des tests et utiliser des outils de qualité comme des linters ou des scanners de sécurité.
 
### Sécurité et confidentialité
 
Avec Ollama en local, les données restent sur la machine, ce qui limite les risques de fuite vers le cloud. C’est un avantage pour le code propriétaire et les données sensibles.
 
Cependant, il ne faut jamais mettre de mots de passe, clés API ou secrets dans un prompt. Même en local, des traces peuvent rester dans l’historique, les logs ou les fichiers de Continue.
 
Bonnes pratiques :
 
- ne pas copier de secrets dans les prompts ;
- vérifier le code généré ;
- scanner les dépendances proposées ;
- tester dans un environnement isolé ;
- supprimer les conversations locales si nécessaire.
 
### Performance
 
Pour améliorer la vitesse, il faut choisir un modèle adapté à la tâche. Un petit modèle comme `llama3.2:3b` est rapide pour le chat, tandis que `codellama:7b` est plus adapté au code.
 
Pour améliorer la qualité, il est conseillé d’utiliser une température basse pour le code, par exemple entre `0.2` et `0.4`, afin d’obtenir des réponses plus stables.
 
Si la machine manque de RAM, il faut arrêter les modèles inutilisés avec :
 
```powershell
ollama stop <modele>
```
 
### Conclusion
 
L’IA locale est un bon assistant pour générer, expliquer ou améliorer du code. Elle permet de gagner du temps, mais elle ne remplace pas le développeur. Le code généré doit toujours être relu, testé et validé avant d’être utilisé dans un projet réel.

## Partie 8 : Reflexion ethique, legale et RGPD

Scenario 1 : Confidentialite des donnees
1. Quels principes RGPD sont concernes ?
   - Minimisation des donnees, confidentialite, finalite du traitement, securite et transparence. 

2. Ollama local stocke-t-il les conversations ? Ou ?
   - Ollama local ne les envoie pas au cloud. Les traces peuvent rester sur la machine selon les outils utilises, par exemple dans l'historique du terminal, VS Code ou Continue.

3. Quelles differences avec ChatGPT cloud ?
   - Avec Ollama, les donnees restent localement. Avec ChatGPT cloud, les donnees sont envoyees vers un service externe, selon les conditions du fournisseur.
 
4. Comment documenter l'utilisation d'IA dans le registre CNIL ?
   - Indiquer la finalite, les donnees traitees, les utilisateurs, les outils IA, la base legale, les mesures de securite et la duree de conservation.

Scenario 2 : Propriete intellectuelle
1. Qui possede le code genere ? L'entreprise ? Le developpeur ? Meta/Mistral ?
   - En general, le code appartient a l'organisation ou au developpeur qui l'integre, mais il faut verifier le contrat de travail et les licences des modeles.
 
2. Peut-on utiliser ce code dans un produit commercial ?
   - Oui si les licences du modele et des dependances le permettent, et apres verification humaine du code.
 
3. Faut-il mentionner l'utilisation d'IA dans la documentation ?
   - C'est recommande pour la transparence, surtout dans un contexte professionnel ou scolaire.
 
4. Quelles sont les licences des modeles utilises ?
   - Elles dependent du modele : Llama, CodeLlama, Mistral et Nomic ont chacun leurs propres licences a consulter avant usage commercial.

Scenario 3 : Biais algorithmiques
1. Comment detecter les biais dans le code genere ?
   - Relire le code, tester plusieurs cas limites, verifier les donnees utilisees et faire une revue par un humain.
 
2. Quelle responsabilite du developpeur qui valide ce code ?
   - Le developpeur reste responsable du code livre, meme si une IA l'a propose.
 
3. Comment signaler ces problemes aux createurs de modeles ?
   - Via les depots GitHub, formulaires de feedback, forums officiels ou canaux de support du fournisseur.
 
4. Exemples de biais courants :
   - Hypotheses implicites, noms stereotypes, mauvais traitement de certaines langues, exemples non inclusifs, logique injuste sur certaines donnees.

Scenario 4 : Transparence et traçabilite
1. Doit-on informer les developpeurs que leur code est analyse ?
   - Oui, surtout si l'analyse est automatique ou conservee.
 
2. Faut-il une politique d'utilisation de l'IA ?
   - Oui, pour definir les usages autorises, les donnees interdites, la validation humaine et les responsabilites.
 
3. Comment tracer quelle partie du code est generee par IA ?
   - Avec des commits separes, commentaires, tickets, notes de revue ou mention dans la documentation projet.
 
4. AI Act : quel niveau de risque pour cet usage ?
   - Pour l'aide au developpement, le risque est generalement limite, sauf si le code concerne un domaine sensible ou a fort impact.

Le fichier "reflexion-ethique-tp1.md" résume toutes c'est question comme demandé dans le TP1, ce fichier ce trouve dans le même dossier.