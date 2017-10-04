---
title: SQL Server Management Studio - Journal des modifications (SSMS) | Microsoft Docs
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3dc76cc1-3b4c-4719-8296-f69ec1b476f9
caps.latest.revision: 72
author: stevestein
ms.author: sstein
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: f12afa26bb406a17c41059b12cc8e1b7a9c411a1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/21/2017

---
# <a name="sql-server-management-studio---changelog-ssms"></a>SQL Server Management Studio - Journal des modifications (SSMS)

Cet article fournit des détails sur les mises à jour, les améliorations et les correctifs de bogues des versions actuelles et précédentes de SSMS. Téléchargez les [versions précédentes de SSMS ci-dessous](#previous-ssms-releases).

## <a name="ssms-172download-sql-server-management-studio-ssmsmd"></a>[SSMS 17.2](download-sql-server-management-studio-ssms.md)

Disponibilité générale | Numéro de build : 14.0.17177.0

### <a name="enhancements"></a>Améliorations

- L’authentification multifacteur (MFA)
  - L’authentification de plusieurs utilisateurs Azure AD pour une authentification universelle avec l’authentification multifacteur (agent utilisateur avec MFA)
  - Un nouveau champ d’entrée des informations d’identification de l’utilisateur a été ajouté pour l’authentification universelle avec MFA afin de prendre en charge l’authentification de plusieurs utilisateurs.
- La boîte de dialogue de connexion prend désormais en charge les 5 méthodes d’authentification suivantes :
  - Authentification Windows
  - Authentification SQL Server
  - Active Directory - Authentification universelle avec prise en charge de MFA
  - Active Directory - Authentification par mot de passe
  - Active Directory - Authentification intégrée

- L’Assistant Importation/exportation de base de données pour DacFx utilisant l’authentification universelle avec MFA.
- Pour la prise en charge de l’API, consultez [IUniversalAuthProvider Interface](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx) (Interface IUniversalAuthProvider).
- La bibliothèque ADAL gérée, utilisée par l’authentification universelle Azure AD avec MFA, a été mise à niveau vers la version 3.13.9.
- Par ailleurs, une nouvelle interface CLI a été publiée, prenant en charge le paramètre d’administration Azure AD pour SQL Database et SQL Data Warehouse.

 Pour plus d’informations sur les méthodes d’authentification Active Directory, consultez [Authentification universelle avec SQL Database et SQL Data Warehouse (prise en charge de SSMS pour MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication) et [Configurer l’authentification multifacteur Azure SQL Database pour SQL Server Management Studio](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure).

- La fenêtre Sortie a des entrées pour les requêtes exécutées pendant le développement des nœuds de l’Explorateur d’objets
- Concepteur de vues activé pour les bases de données Azure SQL Database
- Les options de script par défaut pour les objets de script dans l’Explorateur d’objets de SSMS ont changé :
  - Avant, la valeur par défaut pour une nouvelle installation spécifiait que le script généré devait cibler la dernière version de SQL Server (actuellement SQL Server 2017).
  - Dans SSMS 17.2, une nouvelle option a été ajoutée : *Faire correspondre les paramètres de script à la source*. Quand la valeur est définie sur *True*, le script généré cible les mêmes version, type de moteur et édition de moteur que le serveur à partir duquel l’objet est scripté.
  - Comme la valeur de *Faire correspondre les paramètres de script à la source* est définie sur *True* par défaut, les nouvelles installations de SSMS scriptent toujours automatiquement par défaut les objets sur la même cible que celle du serveur d’origine.
  - Quand la valeur de *Faire correspondre les paramètres de script à la source* est définie sur *False*, les options de cible de script normales sont activées et fonctionnent comme avant.
    - Par ailleurs, toutes les options de script ont été déplacées dans leur propre section - *Options de version*. Elles ne sont plus sous *Options de script générales*.

- Nouvelle prise en charge des clouds nationaux dans « Restaurer à partir de l’URL »
- Les rapports QueryStoreUI prennent désormais en charge des métriques supplémentaires (RowCount, DOP, CLR Time, etc.) de sys.query_store_runtime_stats.
- IntelliSense est maintenant pris en charge par Azure SQL Database
    - https://connect.microsoft.com/SQLServer/feedback/details/3100677/ssms-2016-would-be-nice-to-have-intellisense-on-azure-sql-databases
- Sécurité : par défaut, la boîte de dialogue de connexion ne fait pas confiance aux certificats de serveur et demande le chiffrement des connexions Azure SQL Database
- Améliorations générales de la prise en charge de SQL Server sur Linux :
 - Le nœud Messagerie de base de données est de retour
 - Différents problèmes concernant les chemins ont été traités
 - Le moniteur d’activité est plus stable
 - La boîte de dialogue Propriétés de connexion affiche la plateforme appropriée
- Le rapport de serveur Tableau de bord des performances est désormais disponible comme rapport par défaut :
  - Peut se connecter à SQL Server 2008 et versions ultérieures.
  - Le sous-rapport Index manquants utilise la notation pour permettre d’identifier les index plus utiles.
  - Le sous-rapport Historique des statistiques d’attente regroupe maintenant les attentes par catégorie. Les attentes d’inactivité et de mise en veille sont filtrées par défaut.
  - Nouveau sous-rapport Historique des verrous.
- La recherche de nœuds de plan d’exécution de requêtes permet d’effectuer des recherches dans les propriétés de plan. Recherchez facilement n’importe quelle propriété d’opérateur, comme un nom de table. Pour utiliser cette option quand vous affichez un plan :
  - Cliquez avec le bouton droit sur le plan et, dans le menu contextuel, cliquez sur l’option Rechercher un nœud
  - Utiliser Ctrl+F


### <a name="analysis-services-as"></a>Analysis Services (AS)

- Une nouvelle sélection de membre du rôle AAD a été ajoutée pour les utilisateurs sans adresse e-mail dans les modèles Azure AS dans SSMS

### <a name="integration-services-is"></a>Integration Services (IS)

- Ajout d’une nouvelle colonne (« Nombre d’exécutions ») dans le rapport d’exécution de SSIS

### <a name="known-issues-in-this-release"></a>Problèmes connus dans cette version :

- Les fenêtres de requête qui utilisent l’authentification « Active Directory – Authentification universelle avec prise en charge de MFA » peuvent rencontrer une erreur similaire à la suivante, quand vous tentez d’exécuter une requête ouverte depuis une heure :

   `Msg 0, Level 11, State 0, Line 0
The connection is broken and recovery is not possible. The client driver attempted to recover the connection one or more times and all attempts failed. Increase the value of ConnectRetryCount to increase the number of recovery attempts.`

   La réexécution de la requête doit permettre de surmonter l’erreur.

- Les fonctionnalités SSMS suivantes ne sont pas prises en charge pour l’authentification Azure AD qui utilise l’authentification universelle avec MFA :
  - Le concepteur **Nouvelle table/vue** affiche l’ancienne invite de connexion et ne fonctionne pas pour l’authentification Azure AD.
  - La fonctionnalité **Modifier les 200 premières lignes** ne prend pas en charge l’authentification Azure AD.
  - Le composant **Serveur inscrit** ne prend pas en charge l’authentification Azure AD.
  - L’**Assistant Paramétrage du moteur de base de données** n’est pas pris en charge pour l’authentification Azure AD. Il existe un problème connu où le message d’erreur présenté à l’utilisateur est loin d’être utile : *Impossible de charger le fichier ou l’assembly ’Microsoft.IdentityModel.Clients.ActiveDirectory,...* au lieu du message attendu : *L’Assistant Paramétrage du moteur de base de données ne prend pas en charge Microsoft Azure SQL Database. (DTAClient)* .

**AS**

- L’Explorateur d’objets dans SSAS n’affiche pas le nom d’utilisateur de l’authentification Windows dans les propriétés de connexion d’Azure AS.

### <a name="bug-fixes"></a>Correctifs de bogues

- Correction d’un problème quand vous tentez d’imprimer les résultats d’une requête (sous forme de texte).  https://connect.microsoft.com/SQLServer/feedback/details/3055225/
- Correction d’un problème où SSMS supprimait sans raison des tables et d’autres objets lors de la mise en script de la suppression de ces objets sur une base de données SQL Azure.
- Correction d’un problème où SSMS refusait parfois de démarrer avec une erreur de type « Un ou plusieurs composants introuvables. Réinstallez l’application »
- Correction d’un problème où le SPID dans l’IU SSMS pouvait devenir obsolète et désynchronisé. https://connect.microsoft.com/SQLServer/feedback/details/1898875
- Correction d’un problème dans le programme d’installation (sans assistance) de SSMS où l’argument /passive était traité comme /quiet.
- Correction d’un problème où SSMS levait parfois une erreur « Référence d’objet non définie sur une instance de l’objet » au démarrage. http://connect.microsoft.com/SQLServer/feedback/details/3134698
- Correction d’un problème avec l’« Assistant Compression de données » qui était à l’origine du blocage de SSMS quand vous appuyiez sur « Calculer » sur la table graphique
- Correction d’un problème de performances quand vous cliquiez avec le bouton droit sur l’index d’une table (avec une connexion Internet lente). https://connect.microsoft.com/SQLServer/feedback/details/3120783
- Correction d’un problème où SSMS ne pouvait pas énumérer les fichiers de sauvegarde sur les serveurs avec un classement respectant la casse. http://connect.microsoft.com/SQLServer/feedback/details/3134787 et https://connect.microsoft.com/SQLServer/feedback/details/3137000
- Corrections assorties pour le plan d’exécution de requêtes et la comparaison de plans d’exécution de requêtes
- Correction d’un problème où la boîte de dialogue Connexion ne permettait pas à l’utilisateur de spécifier le « Protocole réseau » à utiliser pour la connexion, à moins que SQL Server ne soit installé sur l’ordinateur exécutant SSMS. https://connect.microsoft.com/SQLServer/feedback/details/3134997
- Amélioration de la prise en charge des configurations multimoniteurs où des boîtes de dialogue SSMS s’affichaient dans des emplacements « aléatoires ». Ajout d’une nouvelle option « Boîtes de dialogue de tâches » sous les paramètres utilisateur « Explorateur d’objets SQL Server | Commandes » pour permettre la mémorisation de la position d’une boîte de dialogue de tâche ou d’une feuille de propriétés quand elle se ferme. https://connect.microsoft.com/SQLServer/feedback/details/889169, https://connect.microsoft.com/SQLServer/feedback/details/1158271, https://connect.microsoft.com/SQLServer/feedback/details/3135260 
- Correction d’un problème où SSMS ne pouvait pas changer les propriétés d’une base de données Azure SQL Database chiffrée
- Amélioration de l’option « Ignorer les résultats après l’exécution ». https://connect.microsoft.com/SQLServer/feedback/details/1196581
- Amélioration/correction d’un problème où les utilisateurs ne pouvaient pas accéder aux abonnements Azure pour lesquels ils n’étaient pas administrateurs.
- Amélioration de l’Assistant « Restauration de la base de données » pour que la base de données cible reste sélectionnée dans l’Explorateur d’objets, indépendamment de la sélection de la base de données source. https://connect.microsoft.com/SQLServer/feedback/details/3118581
- Correction d’un problème où l’Explorateur d’objets ne triait pas correctement les « Procédures stockées compilées en mode natif » récemment ajoutées. http://connect.microsoft.com/SQLServer/feedback/details/3133365
- Correction d’un problème où « SÉLECTIONNER LES N PREMIÈRES LIGNES » n’incluait pas la clause « TOP ». Pour Azure SQLDW. https://connect.microsoft.com/SQLServer/feedback/details/3133551 et https://connect.microsoft.com/SQLServer/feedback/details/3135874
- QueryStoreUI : Correction d’un problème où les intervalles de temps non personnalisés ne fonctionnaient pas correctement pour tous les rapports.
- Always Encrypted :
    - Amélioration de la messagerie pour l’état de l’autorisation AKV dans la boîte de dialogue Nouvelle clé CMK
    - Ajout d’info-bulles à la liste déroulante des clés CEK pour faciliter la distinction des clés CEK avec des noms longs
    - Correction d’un problème où certains fournisseurs de magasin de clés CNG n’étaient pas affichés dans la boîte de dialogue Nouvelle clé principale de colonne pour Always Encrypted
- Correction du « Nom d’application » incohérent pour les connexions SSMS. http://connect.microsoft.com/SQLServer/feedback/details/3135115
- Correction d’un problème où SSMS ne générait pas de scripts corrects pour SQL Azure (tables et index avec l’option DATA_COMPRESSIONS). https://connect.microsoft.com/SQLServer/feedback/details/3133148
- Correction d’un problème où l’utilisateur ne pouvait pas utiliser le raccourci CTRL+Q pour le Lancement rapide (Remarque : Les nouvelles combinaisons de touches pour activer/désactiver l’option « IntelliSense activé » dans l’éditeur de requête sont désormais CTRL+B, CTRL+I.) https://connect.microsoft.com/SQLServer/feedback/details/3131968
- Correction d’un problème dans la « Restauration de base de données » où SSMS levait une exception au moment de sélectionner un compte de stockage à partir d’un abonnement avec des comptes associés à des domaines personnalisés définis
- Correction d’un problème dans « Diagramme de base de données » où SSMS levait une erreur « L’index était en dehors des limites du tableau ». Par ailleurs, l’utilisateur pouvait seulement changer la « vue Table » en vue standard. https://connect.microsoft.com/SQLServer/feedback/details/3133792 et http://connect.microsoft.com/SQLServer/feedback/details/3135326
- Correction d’un problème dans « Sauvegarde/restauration vers l’URL » où SSMS n’énumérait pas les comptes de stockage classiques.
- Correction d’un problème où une exception était levée lors de la tentative d’ajout d’éléments sécurisables liés à un schéma à des rôles de base de données. https://connect.microsoft.com/SQLServer/feedback/details/3118143
- Correction d’un problème où SSMS affichait par intermittence l’erreur « Les données sont de type Null. Cette méthode ou propriété ne peut pas être appelée sur des valeurs Null. » lors du développement d’un nœud de table http://connect.microsoft.com/SQLServer/feedback/details/3136283
- DTA : Correction d’un problème où DTAEngine.exe se terminait avec une altération du tas lors de l’évaluation de la fonction de partition avec certaines valeurs limites.


Analysis Services (AS)
- Correction d’un problème où la commande AS Restaurer la base de données échouait avec une erreur si la base de données avait un nom différent de l’ID
- Correction d’un problème où la fenêtre de requête DAX ignorait l’option de menu permettant d’activer/désactiver IntelliSense activé
- Correction d’un problème qui empêchait de se connecter à SSAS avec des adresses http/https msmdpump IIS
- Autorisation de la connexion à Azure AS à l’aide d’un mot de passe contenant un point-virgule
- Le script de la commande AS Restaurer la base de données avec l’option « Ignorer l’appartenance » inclut la nouvelle option JSON correspondante quand il est utilisé avec le serveur SQL Server 2017 AS ou Azure AS
- Correction d’un problème très rare où la boîte de dialogue de suppression de base de données levait une erreur lors du chargement
- Correction d’un problème qui pouvait se produire quand vous tentiez d’afficher des partitions dans le modèle de niveau de compatibilité 1400 contenant un mélange de définitions de requête SQL et de partition M

Integration Services (IS)
- Correction d’un problème où il était impossible d’afficher les rapports d’informations sur l’exécution du catalogue SSISDB
- Correction de problèmes dans SSMS relatifs aux performances médiocres liées à un grand nombre de projets/packages


## <a name="previous-ssms-releases"></a>Versions précédentes de SSMS

Téléchargez les versions précédentes de SSMS en cliquant sur le lien des titres dans les sections suivantes.

## <a name="downloadssdtmediadownloadpng-ssms-171httpsgomicrosoftcomfwlinklinkid849819"></a>![télécharger](../ssdt/media/download.png) [SSMS 17.1](https://go.microsoft.com/fwlink/?linkid=849819)
Disponibilité générale | Numéro de build : 14.0.17119.0

### <a name="enhancements"></a>Améliorations

- Profileur : Aide > À propos de affiche maintenant le numéro de version (par exemple 17.1)
- Les utilisateurs Analysis Service peuvent actualiser les informations d’identification de leurs sources de données pour les modèles 1200 TM et supérieur dans le menu contextuel sur la source de données.
- Les rapports SSIS prédéfinis montrent maintenant les journaux de l’exécution de SSIS Scale Out dans CTP 2.1
- Application de gestion de SSIS Scale Out
  - Affichez les informations de base de Scale Out Master.
  - Ajoutez facilement un worker au déploiement de Scale Out.
  - Affichez tous les Scale Out workers et les informations de base les concernant. Vous pouvez aussi les activer ou les désactiver facilement.

### <a name="bug-fixes"></a>Correctifs de bogues
- AlwaysOn :
  - Correction d’un problème où les propriétés d’un réplica de disponibilité étaient toujours affichées avec le mode « Basculement automatique » pour les groupes de disponibilité WSFC.
  - Correction d’un problème où la liste de routage en lecture seule était remplacée lors de la mise à jour du groupe de disponibilité
- Always Encrypted : correction d’un problème où des informations générées par DacFx étaient manquantes dans le fichier journal généré.
- ShowPlan : correction d’un problème où l’interface utilisateur affichait toujours l’attribut de type de jointure réel pour les opérateurs de jointure non adaptatifs.
- Programme d’installation :
  - Correction d’un problème où SSMS 17.0 endommageait SSDT sur Visual Studio 2013 [Article de Microsoft Connect 3133479]
  - Correction d’un problème où cliquer sur « Redémarrer » à la fin du programme d’installation ne redémarrait pas la machine
- Script : empêchement temporaire de la suppression accidentelle d’objets de base de données Azure par SSMS lors de la création d’un script de suppression, via la désactivation de cette option.  Un correctif approprié sera apporté dans une prochaine version de SSMS.
- Explorateur d’objets : correction d’un problème où le nœud « Bases de données » n’était pas développé lors de la connexion à une base de données Azure créée avec « AS COPY »

## <a name="downloadssdtmediadownloadpng-ssms-170httpgomicrosoftcomfwlinklinkid847722"></a>![télécharger](../ssdt/media/download.png) [SSMS 17.0](http://go.microsoft.com/fwlink/?LinkID=847722)
Disponibilité générale | Numéro de build : 14.0.17099.0

### <a name="enhancements"></a>Améliorations 

- Package de mise à niveau et Windows Software Update Services (WSUS) 
    - Les versions futures 17.X incluront un package de mises à jour cumulatives plus petit 
  - Le package de mise à jour sera également publié sur le catalogue WSUS  
- Mises à jour des icônes
    - Des icônes ont été mises à jour pour être cohérentes avec les icônes fournies par le Shell Visual Studio. Elles prennent en charge des résolutions élevées.
    - Nouvelles icônes de programme SSMS et Profiler permettant de différencier les versions 16.X et 17.X
- Module SQL PowerShell
  - Le module PowerShell SQL Server a été supprimé de SSMS et est désormais fourni via PowerShell Gallery (PowerShell 5.0 est maintenant obligatoire pour la prise en charge de la gestion des versions des modules)
  - Améliorations diverses à la « présentation » (mise en forme) de certains objets SMO (par exemple, les bases de données indiquent désormais la taille et la quantité d’espace disponible, et les tables indiquent le nombre de lignes et l’utilisation de l’espace)
  - Colorisation ajoutée quand l’invite de commandes PowerShell est appelée à partir du menu « Démarrer PowerShell » dans l’Explorateur d’objets
  - Les paramètres ClusterType et -RequiredCopiesToCommit ont été ajoutés aux applets de commande AG (New-SqlAvailabilityGroup, Join-SqlAvailabilityGroup, et les applets de commande Set-SqlAvailabilityGroup)
  - Les paramètres - ActiveDirectoryAuthority et - AzureKeyVaultResourceId ont été ajoutés à l’applet de commande Add-SqlAzureAuthenticationContext
  - Ajout des applets de commande Revoke-SqlAvailabilityGroupCreateAnyDatabase, Grant-SqlAvailabilityGroupCreateAnyDatabase et Set-SqlAvailabilityReplicaRoleToSecondary
  - Ajout du paramètre SeedingMode aux applets de commande Set-SqlAvailabilityReplica et New-SqlAvailabilityReplica
  - Ajout du paramètre -ConnectionString à Get-SqlDatabase
- SQL Server sur Linux
    - Améliorations d’ordre général et correctifs pour la copie des journaux de transaction
  - Ajout de la prise en charge des chemins Linux natifs pour attacher, sauvegarder et restaurer une base de données
  - Ajout de la prise en charge des chemins Linux natifs pour le dossier de destination du journal d’audit
- Analysis Services
  - Fenêtre de requête DAX :
    - Mise en correspondance des parenthèses dans l’éditeur
    - Prise en charge de la syntaxe DEFINE MEASURE et DEFINE VAR
    - Différentes améliorations apportées à Intellisense
  - Authentification universelle
    - Permet aux utilisateurs de spécifier un nom d’utilisateur et aucun mot de passe : la boîte de dialogue de connexion d’Azure gère alors la connexion
  - Intégration de PQ SSMS : 
    - Écriture de scripts de travaux de sources de données structurées 
    - Affichage et modification de sources de données structurées dans l’interface utilisateur de PQ
- Nouveau modèle « Ajouter une contrainte Unique »
- Showplan
    - Affichage du maximum au lieu de la somme pour les threads dans la fenêtre Propriétés
    - Affichage des propriétés du nouvel opérateur d’allocation de mémoire
    - Activation du bouton Modifier la requête dans les statistiques des requêtes dynamiques
    - Prise en charge de l’exécution entrelacée
  - Nouvelle option pour « Analyser le plan d’exécution réel »
  - Améliorations générales apportées à la comparaison du plan d’exécution de requêtes
  - Une fonction a été introduite dans la fonctionnalité de comparaison de plan d’exécution de requêtes pour rechercher des différences significatives dans l’estimation de la cardinalité entre les nœuds correspondants de deux plans de requête et pour effectuer une analyse des causes principales possibles.
- Suppression du gestionnaire de configuration à partir de l’Explorateur de serveurs inscrits
- Activation de la lecture des journaux d’audit à partir du stockage d’objets blob Azure
- Un paramétrage a été ajouté pour Always Encrypted. Reportez-vous à [cette page](https://blogs.msdn.microsoft.com/sqlsecurity/2016/12/13/parameterization-for-always-encrypted-using-ssms-to-insert-into-update-and-filter-by-encrypted-columns/) pour plus de détails 
- La connexion d’authentification universelle AAD à Azure SQL Database prend en charge les ID de locataire personnalisés 
- La génération de scripts pour Azure SQL Database inclut désormais le texte intégral, les règles et la base de données
- Correctifs de la personnalisation dans les écrans de démarrage pour SSMS et le profileur
- Suppression dans SSMS de l’interface utilisateur du point de contrôle de l’utilitaire
- SSMS peut maintenant créer des bases de données SQL Azure dans l’édition « PremiumRS »
- Groupes de disponibilité AlwaysOn
  - Ajout de la prise en charge pour de nouveaux types de cluster : EXTERNAL et NONE
    - Ajout de la prise en charge de SQL Server sur Linux
    - Ajout de l’amorçage automatique comme option pour la synchronisation initiale des données
    - Correction de certains problèmes, par exemple la gestion des URL des points de terminaison, l’actualisation des bases de données et la présentation de l’interface utilisateur
    - Suppression de fonctionnalités relatives aux réplicas Azure
  - Amélioration d’IntelliSense pour plusieurs mots clés des groupes de disponibilité
- Moniteur d'activité
  - Ajout d’un nouveau volet « Moniteur d’activité » à la fenêtre de sortie de SSMS
  - Modification du message d’erreur/de dépassement du délai d’expiration de connexion pour consigner des informations dans la fenêtre de sortie au lieu d’afficher un message contextuel
  - Suppression du graphique vide (graphique 5) dans la section Vue d’ensemble
  - Ajout de « (en pause) » au titre Vue d’ensemble si la collecte de données du moniteur d’activité est mise en pause
  - Extensions de graphe SQL Server 
    - Nouvelles icônes pour les tables de nœuds et d’arêtes de graphe
    - Les tables de nœuds et d’arêtes de graphe sont affichées sous le dossier Tables graphiques
    - Disponibilité de modèles pour créer des tables de nœuds et d’arêtes de graphe
- Mode de présentation
    - 3 nouvelles tâches disponibles via le menu de lancement rapide (CTRL-Q)
    - PresentOn - Activation du mode de présentation
    - PresentEdit - Modification de la taille des polices pour le mode de présentation.  « Police Éditeur de texte » pour l’éditeur de requête.  « Police Environnement » pour les autres composants.
    - RestoreDefaultFonts - Rétablissement des paramètres par défaut.
    - *Remarque : il n’existe actuellement aucune commande PresentOff pour l’instant.  Utiliser RestoreDefaultFonts pour désactiver le mode de présentation*

### <a name="bug-fixes"></a>Correctifs de bogues

- Correction d’un problème où SSMS se bloquait quand l’utilisateur faisait défiler le plan d’exécution de requêtes via le pavé tactile d’un Surface Book
- Correction d’un problème où SSMS se bloquait pendant un long moment lors de l’obtention des propriétés d’une base de données en cours de restauration ou hors connexion 
- Correction d’un problème où la « Visionneuse d’aide » ne pouvait pas être ouverte dans les builds RC
- Correction d’un problème où les éléments de la « Boîte à outils des tâches des plans de maintenance » peuvent être manquants dans SSMS.
- Correction d’un problème dans SSMS où l’utilisateur ne pouvait pas réduire une base de données quand le nom de cette base de données contenait des accolades. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3122618)
- Correction d’un problème où SSMS, au moment où il essayait de créer un script pour supprimer une base de données Azure, provoquait la suppression de la base de données elle-même. [Article de Microsoft Connect](http://connect.microsoft.com/SQLServer/feedback/details/3131458/)
- Correction d’un problème où les valeurs par défaut n’ont pas fait l’objet d’un script pour les types de tables définis par l’utilisateur. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3119027)
- Autre série d’améliorations des performances liées au menu contextuel des index. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3120783)
- Correction du problème qui provoquait un scintillement excessif lorsque des index manquants du plan d’exécution faisaient l’objet d’un pointage de la souris. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3118510)
- Correction d’un problème où SSMS prenait la base de données hors connexion lors de l’écriture de scripts [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3118550)
- Divers correctifs liés à l’interface utilisateur sur les versions localisées (dans une langue que l’anglais) de SSMS.
- Correction du problème où le nœud de « Always Encrypted Keys » était manquant lors du ciblage de SQL 2016 SP1 Édition Standard.
- Always Encrypted
    - Activation incorrecte du menu Always Encrypted lors du ciblage de SQL 2016 RTM Édition Standard ou de n’importe quel serveur SQL 2014 (et versions antérieures)
    - Correction d’un problème où IntelliSense signale une erreur lors de l’utilisation de la syntaxe CREATE ou ALTER
    - Correction du problème où le chiffrement échoue si CMK/CEK contient des caractères qui devraient être ignorés, par exemple mis entre crochets
    - En cas d’exception liée à une mémoire insuffisante dans SSMS, l’utilisateur reçoit une erreur proposant d’utiliser le module PowerShell (64 bits) natif.
    - Correction du problème lié à l’échec de l’Assistant AE si l’utilisateur a utilisé des abonnements de responsable de groupe de ressources au lieu d’abonnements Azure classiques
    - Correction du problème où l’Assistant AE affiche une erreur incorrecte lorsque l’utilisateur ne détient aucune autorisation dans le cadre de ces abonnements ni aucun coffre de clé Azure.
    - Correction d’un problème de l’Assistant AE où la page de connexion du coffre de clé Azure n’affiche pas les abonnements Azure en présence de plusieurs AAD
    - Correction d’un problème de l’Assistant AE où la page de connexion du coffre de clé Azure n’affiche pas les abonnements Azure pour lesquels l’utilisateur détient une autorisation de lecture
  - Correction d’un problème où les fichiers de ressources ne pouvaient pas être chargés correctement, ce qui provoquait des messages d’erreur imprécis
- Amélioration du contraste des liens hypertexte sur la page Installation de SSMS
- Correction d’un problème lié au non-affichage des nœuds Polybase lors de la connexion à SQL Server Express (2016 SP1)
- Correction d’un problème où SSMS ne pouvait pas changer le niveau de compatibilité d’une base de données Azure pour le faire passer à v140
- Amélioration des performances de l’Explorateur d’objets lors du développement de la liste des bases de données Azure [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3100675)
- Correction d’un problème où l’élément de menu contextuel Afficher le journal SQL Server apparaît de manière incorrecte pour les types de serveurs non relationnels (AS\RS\IS) 
- Correction d’un problème dans lequel la vérification de la syntaxe d’une requête de partition Analysis Services à l’aide de l’authentification SQL pouvait entraîner un message d’échec de connexion
- Correction d’un problème dans lequel le fait de renommer un modèle tabulaire AS de niveau de compatibilité 1400 d’aperçu pouvait échouer dans SSMS
- Correction d’un problème lié au message « échec de l’opération sur le modèle » qui pouvait se produire après avoir tenté une opération non valide sur le serveur AS dans de rares circonstances et rétablir les modifications locales suite à un échec d’enregistrement sur le modèle
- Correction d’une faute d’orthographe dans la boîte de dialogue contextuelle de synchronisation des bases de données Analysis Services
- Les boîtes de dialogue de sauvegarde/restauration de conteneur se trouvent en dehors de l’écran dans les configurations avec plusieurs moniteurs. 
- La création d’une stratégie de sécurité échoue si le nom de l’objet cible contient le caractère « ] ».
- Le menu « Ouvrir un fichier récent » de SSMS 2016 n’affiche pas les fichiers récemment enregistrés. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)
- Suppression de la réinitialisation des paramètres utilisateur lors de la mise à jour du shell VS.
- Correction d’un problème qui empêchait l’utilisateur de pouvoir changer le niveau de compatibilité d’une base de données sur SQL Server 2017.
- Les fenêtres de requête utilisant l’authentification universelle AAD ne peuvent pas actualiser la requête au bout d’une heure.
- Suppression dans SSMS de l’interface utilisateur du point de contrôle de l’utilitaire.
- Les connexions d’authentification universelle AAD échouent à interroger des données après l’expiration du jeton initial.
- Impossible de générer des scripts de règles depuis Azure SQL Database vers Azure SQL Database.
- Résolution d’un problème où PowerShell SQL ne pouvait pas se connecter à des instances SQL héritées (2014 et antérieur). [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/1138754/sql-server-sqlps-powershell-module-fails-connection-to-sql-2012-instance)
- Résolution d’un problème qui provoquait le blocage de SSMS lors d’un échec d’importation des serveurs inscrits.
- Résolution d’un problème qui provoquait le blocage de SSMS si un utilisateur avait certaines autorisations sur une base de données. 
- SSMS - des tables disparaissent de l’aire de conception pendant l’examen des vues. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/2946125/ssms-tables-disappears-from-design-surface-while-reviewing-views) 
- La barre de défilement des tables ne permet pas à l’utilisateur de faire défiler le contenu d’une table : seule la flèche haut/bas le permet. Il est également possible de faire défiler le contenu de la table après avoir essayé de faire défiler à l’aide de la barre de défilement, ce qui est un bogue. [Article de Microsoft Connect](
http://connect.microsoft.com/SQLServer/feedback/details/3106561/sql-server-manager-2016-bug-in-design-view) 
- Les icônes ne s’affichent pas pour les serveurs inscrits une fois le nœud racine actualisé.
- Le bouton du script pour créer une base de données sur les serveurs v12 Azure exécute un script, puis affiche le message « Aucune action pour le script ».
- La boîte de dialogue SSMS Se connecter au serveur n’efface pas l’onglet « Propriétés supplémentaires » pour chaque nouvelle connexion.
- Le script de génération de tâches ne génère pas de scripts de création de base de données pour une base de données Azure SQL Database.
- La barre de défilement du Concepteur de vues apparaît désactivée.
- Les chemins de clés AVK d’Always Encrypted n’incluent pas les ID de version.
- Réduction du nombre de requêtes de l’édition du moteur dans la fenêtre de requête. [Article de Microsoft Connect](http://connect.microsoft.com/SQLServer/feedback/details/3113387)
- Les erreurs Always Encrypted provenant de l’actualisation des modules après chiffrement ne sont pas gérées correctement.
- Changement du délai d’expiration de la connexion par défaut pour OLTP et OLAP de 15 à 30 secondes, pour résoudre une classe d’échecs de connexion ignorés. 
- Correction d’un blocage dans SSMS lors du lancement d’un rapport personnalisé. [Article de Microsoft Connect](http://connect.microsoft.com/SQLServer/feedback/details/3118856)
- Résolution d’un problème où « Générer un Script... » échoue pour les bases de données SQL Azure.
- Correction de « Générer un script en tant que » et « Assistant Génération de scripts », qui n’ajoutaient pas de sauts de ligne supplémentaires lors de la génération de scripts pour des objets comme les procédures stockées. [Article de Microsoft Connect](http://connect.microsoft.com/SQLServer/feedback/details/3115850)
- Le fournisseur SQLAS PowerShell : Ajout de la propriété LastProcessed aux dossiers Dimension et MeasureGroup. [Article de Microsoft Connect](http://connect.microsoft.com/SQLServer/feedback/details/3111879)
- Statistiques sur les requêtes en direct : Résolution d’un problème où elles montraient seulement la première requête dans un lot. [Article de Microsoft Connect] (http://connect.microsoft.com/SQLServer/feedback/details/3114221)  
- Plan d’exécution de requêtes : Affichage du maximum au lieu de la somme pour les threads dans la fenêtre Propriétés.
- Magasin de requêtes : Ajout d’un nouveau rapport sur les requêtes avec les variation fortes des exécutions.
- Problèmes de performances de l’Explorateur d’objets : [Article de Microsoft Connect](http://connect.microsoft.com/SQLServer/feedback/details/3114074)
    - Le menu contextuel pour les tables se bloque momentanément
    - SSMS est lent quand l’utilisateur clique avec le bouton droit sur un index pour une table (via une connexion (Internet) à distance). 
    - Éviter d’émettre des requêtes sur des tables qui sont triées sur le serveur
- Suppression dans SSMS de l’Assistant Déploiement Azure (pour déployer une base de données sur une machine virtuelle Azure)
- Résolution d’un problème où les index manquants n’étaient pas affichés dans les plans d’exécution dans SSMS [Article de Microsoft Connect](http://connect.microsoft.com/SQLServer/feedback/details/3114194)
- Résolution du problème courant de blocage lors de l’arrêt dans SSMS
- Résolution du problème dans l’Explorateur d’objets, où une erreur se produisait lors de l’affichage du menu contextuel sur les nœuds Polybase | Groupe de scale-out[Article de Microsoft Connect](http://connect.microsoft.com/SQLServer/feedback/details/3115128)
- Résolution d’un problème où SSMS pouvait se bloquer lors d’une tentative d’affichage des autorisations sur une base de données
- Magasin de requêtes : améliorations générales apportées aux éléments du menu contextuel pour les grilles de résultats des rapports du magasin de requêtes
- La configuration d’Always Encrypted pour une table existante échoue avec des erreurs sur des objets non associés. [Article de Microsoft Connect](http://connect.microsoft.com/SQLServer/feedback/details/3103181)
- La configuration d’Always Encrypted pour une base de données existante avec plusieurs schémas ne fonctionne pas. [Article de Microsoft Connect] (http://connect.microsoft.com/SQLServer/feedback/details/3109591)
- L’Assistant Colonne chiffrée d’Always Encrypted échoue parce que la base de données contient des vues qui référencent des vues système. [Article de Microsoft Connect] (http://connect.microsoft.com/SQLServer/feedback/details/3111925)
- Lors du chiffrement à l’aide d’Always Encrypted, les erreurs provenant de l’actualisation des modules après le chiffrement ne sont pas gérées correctement.
- Résolution du problème de troncation de l’interface utilisateur dans la boîte de dialogue « Nouvelle inscription de serveur »
- Correction de la mise à jour incorrecte par l’interface utilisateur des conditions DMF pour les expressions contenant des valeurs de constante de chaîne incluant des guillemets
- Résolution d’un problème pouvant provoquer le blocage de SSMS lors de l’exécution de rapports personnalisés
- Ajout de l’élément de menu « Exécution dans Scale Out... » au nœud du dossier
- Correction d’un problème avec la fonctionnalité des adresses IP de la liste verte de pare-feu SQL Azure DB
- Correction d’un problème dans SSMS qui provoquait une exception de référence d’objet non définie lors de la modification de la source d’une partition multidimensionnelle AS
- Correction d’un problème dans SSMS qui provoquait une exception de référence d’objet non définie lors de la suppression d’un assembly de client d’un serveur AS multidimensionnel
- Correction d’un problème où le renommage d’une base de données 1400 tabulaire AS échouait
- Correction d’un problème de génération de script d’une source de données tabulaire AS de niveau de compatibilité 1400 à partir de la boîte de dialogue des propriétés de connexion
- Suppression de l’hypothèse selon laquelle les tables d’un modèle de niveau de compatibilité 1400 ont au moins une partition
- CTRL+R affiche/masque maintenant le volet de résultats dans l’éditeur de requête SSMS DAX


## <a name="downloadssdtmediadownloadpng-ssms-1653httpgomicrosoftcomfwlinklinkid840946"></a>![télécharger](../ssdt/media/download.png) [SSMS 16.5.3](http://go.microsoft.com/fwlink/?LinkID=840946)
Disponibilité générale | Numéro de build : 13.0.16106.4

Les problèmes suivants ont été résolus dans cette version :

* Résolution du problème introduit dans SSMS 16.5.2 qui provoquait l’expansion du nœud « Table » quand la table comportait plusieurs colonnes éparses.

* Les utilisateurs peuvent déployer des packages SSIS contenant le Gestionnaire de connexions OData qui connectent une ressource Microsoft Dynamics AX/CRM Online au catalogue SSIS. Pour plus d’informations, consultez [Gestionnaire de connexions OData](/sql-docs/docs/integration-services/connection-manager/odata-connection-manager).

* La configuration d’Always Encrypted sur une table existante échoue avec des erreurs sur des objets non associés. [Microsoft Connect - ID 3103181](https://connect.microsoft.com/SQLServer/feedback/details/3103181/setting-up-always-encrypted-on-an-existing-table-fails-with-errors-on-unrelated-objects)

* La configuration d’Always Encrypted pour une base de données existante avec plusieurs schémas ne fonctionne pas. [Microsoft Connect - ID 3109591](https://connect.microsoft.com/SQLServer/feedback/details/3109591/sql-server-2016-always-encrypted-against-existing-database-with-multiple-schemas-doesnt-work)

* L’Assistant Colonne chiffrée d’Always Encrypted échoue parce que la base de données contient des vues qui référencent des vues système. [Microsoft Connect - ID 3111925](https://connect.microsoft.com/SQLServer/feedback/details/3111925/sql-server-2016-always-encrypted-encrypted-column-wizard-failed-task-failed-due-to-following-error-cannot-save-package-to-file-the-model-has-build-blocking-errors)

* Lors du chiffrement à l’aide d’Always Encrypted, les erreurs provenant de l’actualisation des modules après le chiffrement ne sont pas gérées correctement.

* Le menu *Ouvrir un fichier récent* n’affiche pas les fichiers récemment enregistrés. [Microsoft Connect - ID 3113288](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)

* SSMS est lent quand l’utilisateur clique avec le bouton droit sur un index pour une table (via une connexion (Internet) à distance). [Microsoft Connect - ID 3114074](https://connect.microsoft.com/SQLServer/feedback/details/3114074/ssms-slow-when-right-clicking-an-index-for-a-table-over-a-remote-internet-connection)
 
* Correction d’un problème avec la barre de défilement de SQL Designer. [Microsoft Connect - ID 3114856](http://connect.microsoft.com/SQLServer/feedback/details/3114856/bug-in-scrollbar-on-sql-desginer-in-ssms-2016)

* Le menu contextuel pour les tables se bloque momentanément 
 
* Il peut arriver que SSMS lève des exceptions dans le moniteur d’activité et se bloque. [Microsoft Connect - ID 697527](https://connect.microsoft.com/SQLServer/feedback/details/697527/)

* SSMS 2016 se bloque avec l’erreur « Le processus a été arrêté en raison d’une erreur interne dans le runtime .NET à l’adresse IP 71AF8579 (71AE0000) avec le code de sortie 80131506 »


## <a name="ssms-1651"></a>SSMS 16.5.1
Disponibilité générale | Numéro de build : 13.0.16100.1

* Correction d’un problème où Invoke-Sqlcmd insère par erreur plusieurs lignes lors d’une contrainte de validation. [Article Microsoft Connect n°811560](https://connect.microsoft.com/SQLServer/feedback/details/811560)

* Correction d’un problème où les versions en langue autre que le français ne fonctionnent pas complètement lors de la création de groupes de disponibilité.

* Correction d’un problème où un clic sur le fichier XML du plan de requête n’ouvre pas l’interface utilisateur SSMS appropriée.


## <a name="downloadssdtmediadownloadpng-ssms-165httpgomicrosoftcomfwlinklinkid832812"></a>![télécharger](../ssdt/media/download.png) [SSMS 16.5](http://go.microsoft.com/fwlink/?LinkID=832812)
Disponibilité générale | Numéro de build : 13.0.16000.28

* Résolution d’un problème : un blocage peut se produire quand une base de données avec un nom de la table contenant « ;: » a été activée.
* Résolution d’un problème : les modifications apportées à la page Modèle dans la fenêtre des propriétés de base de données tabulaire AS génèrent un script de la définition d’origine. 
[Élément Microsoft Connect : 3080744](https://connect.microsoft.com/SQLServer/feedback/details/3080744) 
* Correction du problème lié à l’ajout de fichiers temporaires à la liste « Fichiers récents ».  
[Élément Microsoft Connect : 2558789](https://connect.microsoft.com/SQLServer/feedback/details/2558789)
* Résolution du problème : l’élément de menu « Gérer la Compression » est désactivé pour les nœuds de la table utilisateur dans l’arborescence de l’Explorateur d’objets.  
[Élément Microsoft Connect : 3104616](https://connect.microsoft.com/SQLServer/feedback/details/3104616)

* Résolution du problème : l’utilisateur ne peut pas définir la taille de police pour l’Explorateur d’objets, l’Explorateur de serveurs inscrits, l’Explorateur de modèle ainsi que pour les détails de l’Explorateur d’objets. La police pour les explorateurs utilise la police de l’environnement.  
[Élément Microsoft Connect : 691432](https://connect.microsoft.com/SQLServer/feedback/details/691432)

* Résolution du problème : SSMS se reconnecte toujours à la base de données par défaut quand la connexion est perdue.  
[Élément Microsoft Connect Item : 3102337](https://connect.microsoft.com/SQLServer/feedback/details/3102337)

* Résolution d’un grand nombre de problèmes liés à la haute résolution dans la fenêtre de gestion des stratégies et de l’Éditeur de requête, notamment les icônes de plan d’exécution.

* Résolution du problème : l’option de configuration des polices et des couleurs pour les événements étendus est manquante.

* Résolution du problème : blocage de SSMS se produisant lors de la fermeture de l’application ou lors de la tentative d’affichage de la boîte de dialogue d’erreur.


## <a name="downloadssdtmediadownloadpng-ssms-1641-september-2016httpgomicrosoftcomfwlinklinkid828615"></a>![télécharger](../ssdt/media/download.png) [SSMS 16.4.1 (septembre 2016)](http://go.microsoft.com/fwlink/?LinkID=828615)
Disponibilité générale | Numéro de build : 13.0.15900.1

*  Correction d’un problème selon lequel la tentative de modification (ALTER) d’une procédure stockée échoue :  
[Article Microsoft Connect n°3103831](https://connect.microsoft.com/SQLServer/feedback/details/3103831)

* Nouvelles applets de commande « Read-SqlTableData », « Read-SqlViewData » et « Write-SqlTableData » pour afficher et écrire des données à l’aide de PowerShell.  
[Trello Read-SqlTableData Card](https://trello.com/c/FXVUNJ8x/131-read-sqltabledata)  
[Article Microsoft Connect n° 2685363](https://connect.microsoft.com/SQLServer/feedback/details/2685363)
    
* Nouvelle applet de commande « Add-SqlLogin » pour permettre de nouveaux scénarios de gestion de connexion à l’aide de PowerShell.  
[Article Microsoft Connect n° 2588952](https://connect.microsoft.com/SQLServer/feedback/details/2588952)
    
*  Prise en charge et utilisation améliorées pour les utilisateurs qui se connectent à plusieurs clouds nationaux.
    
    
*  Correction d’un problème où des exceptions Mémoire insuffisante étaient levées.  
[Article Microsoft Connect n° 3062914](https://connect.microsoft.com/SQLServer/feedback/details/3062914)  
[Article Microsoft Connect n° 3074856](https://connect.microsoft.com/SQLServer/feedback/details/3074856)
    
*  Correction d’un problème où le filtrage par schéma n’était pas une option de filtre valide.  
[Article Microsoft Connect n° 3058105](https://connect.microsoft.com/SQLServer/feedback/details/3058105)  
[Article Microsoft Connect n° 3101136](https://connect.microsoft.com/SQLServer/feedback/details/3101136)
    
*  Correction d’un problème où la fenêtre de surveillance d’une base de données étendue n’était pas accessible.
    
*  Correction d’un problème où la touche F1 (Aide) ouvrait toujours le contenu en ligne. Les utilisateurs peuvent désormais choisir s’ils préfèrent une aide en ligne ou hors connexion dans « Définir les préférences pour l’aide » du menu Aide.   
[Article Microsoft Connect n° 2826366](https://connect.microsoft.com/SQLServer/feedback/details/2826366)
    
*  Correction d’un problème où l’écriture du script d’un modèle tabulaire Analysis Services de niveau 1200 ne supprimait pas le mot de passe pour l’écriture du script, même si la version du serveur indiquait [l’objet de modèle de client est maintenant synchronisé avant l’écriture du script].
    
*  Correction d’un problème où l’option « Sélectionner les n premières lignes » générait une syntaxe déconseillée pour l’opérateur TOP.  
[Article Microsoft Connect n° 3065435](https://connect.microsoft.com/SQLServer/feedback/details/3065435)
    
*  Correction de divers problèmes de mise en page dans SSMS, notamment la page Propriétés de la connexion et les options d’exécution de requête avancée.   
[Article Microsoft Connect n° 3058199](https://connect.microsoft.com/SQLServer/feedback/details/3058199)  
[Article Microsoft Connect n° 3079122](https://connect.microsoft.com/SQLServer/feedback/details/3058199)  
[Article Microsoft Connect n° 3071384](https://connect.microsoft.com/SQLServer/feedback/details/3071384)
    
*  Correction d’un problème où une solution était créée automatiquement chaque fois qu’un utilisateur ouvrait une nouvelle fenêtre de requête.   
[Article Microsoft Connect n° 2924667](https://connect.microsoft.com/SQLServer/feedback/details/2924667)    
[Article Microsoft Connect n° 2917742](https://connect.microsoft.com/SQLServer/feedback/details/2917742)   
[Article Microsoft Connect n° 2612635](https://connect.microsoft.com/SQLServer/feedback/details/2612635)
    
*  Correction d’un problème où les tables temporelles ne pouvaient pas être développées dans l’Explorateur d’objets quand elles se trouvaient dans des bases de données système.  
[Article Microsoft Connect n° 2551649](https://connect.microsoft.com/SQLServer/feedback/details/2551649)
    
*  Correction d’un problème où SSMS exécute une requête SELECT @@trancount après l’exécution d’un lot.    
[Article Microsoft Connect n° 3042364](https://connect.microsoft.com/SQLServer/feedback/details/3042364)
    
*  Correction d’un problème dans Analysis Services où la création d’un script à partir de la page de propriétés d’un serveur masquait une boîte de dialogue de connexion.
    
*  Correction d’un problème où Ctrl + Q ne sélectionnait pas la barre d’outils Lancement rapide.
    
*  Correction d’un problème où la modification du paramètre MaxSize d’une base de données à l’aide de la boîte de dialogue Propriétés du serveur ne fonctionnait pas pour les bases de données > 2 To.  
[Article Microsoft Connect n° 1231091](https://connect.microsoft.com/SQLServer/feedback/details/1231091)
    
*  Correction d’un problème où l’Assistant Restauration de la base de données n’acceptait pas les noms de fichiers avec des espaces de début :   
[Article Microsoft Connect n°2395147](https://connect.microsoft.com/SQLServer/feedback/details/2395147)



## <a name="downloadssdtmediadownloadpng-ssms-163-august-2016httpgomicrosoftcomfwlinklinkid824938"></a>![télécharger](../ssdt/media/download.png) [SSMS 16.3 (août 2016)](http://go.microsoft.com/fwlink/?LinkID=824938)
Généralement disponible | Numéro de version : 13.0.15700.28

* Les versions mensuelles de SSMS sont désormais étiquetées numériquement.

* [Nouvelle option d’authentification **« Authentification universelle Active Directory »**](https://azure.microsoft.com/documentation/articles/sql-database-ssms-mfa-authentication/). Il s’agit d’un système d’authentification par jeton piloté par Azure Active Directory, qui prend en charge des mécanismes d’authentification multifacteur, par mot de passe et intégrée.

* Nouveaux modèles d’événements étendus correspondant à la fonctionnalité des modèles SQL Server Profiler [(article Microsoft Connect n°2543925).](/sql-docs/docs/tools/sql-server-profiler/sql-server-profiler-templates).

* Nouvelles boîtes de dialogue Créer une base de données et Propriétés de la base de données pour les bases de données SQL Azure.

* Nouvelles applets de commande « Get-SqlLogin » et « Remove-SqlLogin » pour effectuer la gestion des comptes de connexion SQL Server à l’aide de PowerShell.  
*Demandes de correctif connexes des clients :*   
[Article Microsoft Connect n°2588952.](https://connect.microsoft.com/SQLServer/feedback/details/2588952/)

* Nouvelle applet de commande PowerShell « New-SqlColumnMasterKeySettings » qui ajoute la prise en charge de la création de clés principales de colonne pour les fournisseurs arbitraires et les chemins d’accès de clé.

* Nouvelle boîte de dialogue « Créer une base de données » pour simplifier la création de bases de données SQL Azure dans SSMS>

* Prise en charge du filtrage dans le nœud « Bases de données » de l’Explorateur d’objets de SSMS. Accédez au nœud « Bases de données » dans l’Explorateur d’objets, puis cliquez sur l’icône de filtre dans la barre d’outils de l’Explorateur d’objet pour filtrer la liste des bases de données.

* Prise en charge des comptes de stockage de type Azure Resource Manager (ARM) dans les Assistants Sauvegarde et Restauration.

* [Prise en charge bêta initiale des écrans haute résolution](https://blogs.msdn.microsoft.com/sqlreleaseservices/ssms-highdpi-support/).  
*Demandes de correctif connexes des clients :*   
[Article Microsoft Connect n°1129301](https://connect.microsoft.com/SQLServer/feedback/details/1129301/management-studio-is-unusable-on-a-4k-display), [Article Microsoft Connect n°1858763](https://connect.microsoft.com/SQLServer/feedback/details/1858763/), [Article Microsoft Connect n°1852671](https://connect.microsoft.com/SQLServer/feedback/details/1852671/), [Article Microsoft Connect n°1487643](https://connect.microsoft.com/SQLServer/feedback/details/1487643/),  [Article Microsoft Connect n°1355641](https://connect.microsoft.com/SQLServer/feedback/details/1355641/), [Article Microsoft Connect n°2161595](https://connect.microsoft.com/SQLServer/feedback/details/2161595/), [Article Microsoft Connect n°1854041](https://connect.microsoft.com/SQLServer/feedback/details/1854041/), [Article Microsoft Connect n°1055617](https://connect.microsoft.com/SQLServer/feedback/details/1055617/), [Article Microsoft Connect n°2448774](https://connect.microsoft.com/SQLServer/feedback/details/2448774/), [Article Microsoft Connect n°1521405](https://connect.microsoft.com/SQLServer/feedback/details/1521405/), [Article Microsoft Connect n°2117853](https://connect.microsoft.com/SQLServer/feedback/details/2117853/), [Article Microsoft Connect n°2014256](https://connect.microsoft.com/SQLServer/feedback/details/2014256/), [Article Microsoft Connect n°2162218](https://connect.microsoft.com/SQLServer/feedback/details/2162218/), [Article Microsoft Connect n°2344551](https://connect.microsoft.com/SQLServer/feedback/details/2344551/), [Article Microsoft Connect n°1664436](https://connect.microsoft.com/SQLServer/feedback/details/1664436/), [Article Microsoft Connect n°2554043](https://connect.microsoft.com/SQLServer/feedback/details/2554043/), [Article Microsoft Connect n°2983216](https://connect.microsoft.com/SQLServer/feedback/details/2983216/), [Article Microsoft Connect n°2021706](https://connect.microsoft.com/SQLServer/feedback/details/2021706/)

* Améliorations de l’Assistant Paramétrage du moteur de base de données (DTA) pour prendre automatiquement en charge la lecture d’une charge de travail à partir du Magasin de requêtes de SQL Server.

* Améliorations de l’Assistant Paramétrage du moteur de base de données (DTA) pour afficher les recommandations d’index des index columnstore, columnstore non cluster et rowstore.

* Prise en charge de l’envoi de commandes DBCC (Database Console Commands) à l’aide d’applets de commande PowerShell de SQL Server Analysis Services.

* Résolution de bogue pour afficher le texte en clair de colonnes d’objet volumineux (LOB) AlwaysEncrypted déchiffrées dans SSMS.  
*Demandes de correctif connexes des clients :*   
[Article Microsoft Connect n°2413024](https://connect.microsoft.com/SQLServer/feedback/details/2413024/cannot-view-cleartext-of-alwaysencrypted-lob-columns-in-ssms)

* Résolution de bogue dans la boîte de dialogue Always Encrypted pour corriger l’incident qui se produit quand les styles visuels Windows ne sont pas activés (par exemple, l’activation de l’affichage à contraste élevé).

* Résolution de bogue pour l’erreur « Méthode introuvable » qui empêche la connexion à des instances SQL Server.

* Résolution de bogue pour l’incident SSMS qui se produit lors de la création d’une fonction de partition avec décalage de date/heure.

* Résolution de bogue pour ajouter l’exigence de disposer de Microsoft .NET 3.5 pour démarrer l’outil d’administration Distributed Replay (DReplay.exe).

* Résolution de bogue dans l’Assistant Déploiement d’Analysis Services pour prendre en charge les noms de serveur complets.

* Résolution de bogue dans SSMS pour afficher les partitions dans les modèles tabulaires Analysis Services avec un modèle de compatibilité 2016.  
*Demandes de correctif connexes des clients :*   
[Article Microsoft Connect n°2845053](https://connect.microsoft.com/SQLServer/feedback/details/2845053/ssms-cannot-display-partitions-in-tabular-models-in-2016-compatibility-level) 

* Améliorations des performances et résolutions de bogues dans les modèles tabulaires Analysis Services et les Objets de gestion partagée SQL Server. 


---
## <a name="downloadssdtmediadownloadpng-ssms-july-2016-hotfix-updatehttpgomicrosoftcomfwlinklinkid822301"></a>![télécharger](../ssdt/media/download.png) [mise à jour du correctif logiciel de SSMS, juillet 2016](http://go.microsoft.com/fwlink/?LinkID=822301)
Généralement disponible | Numéro de version : 13.0.15600.2

* **Résolution de bogue dans SSMS pour activer des options de menu contextuel manquantes**.  
*Demandes de correctif connexes des clients :*  
[Article Microsoft Connect n°2883440](https://connect.microsoft.com/SQLServer/feedback/details/2883440/lost-table-design-and-edit-top-n-rows-in-tables-context-menu)  
[Article Microsoft Connect n°2909644](https://connect.microsoft.com/SQLServer/feedback/details/2909644/ssms-2016-is-missing-edit-options-against-sql-express-2014)  
[Article Microsoft Connect n°2924345](https://connect.microsoft.com/SQLServer/feedback/details/2924345/some-ssms-object-explorer-right-click-menu-options-missing-in-july-update)

---
## <a name="ssms-july-2016"></a>SSMS, juillet 2016 
Généralement disponible | Numéro de version : 13.0.15500.91

* *Modification, 5 juillet :* Amélioration de la prise en charge des bases de données tabulaires SQL Server 2016 (niveau de compatibilité 1200) dans la boîte de dialogue de processus Analysis Services et l’Assistant Déploiement d’Analysis Services.

* *Modification, 5 juillet :* Ajout d’une nouvelle option dans la boîte de dialogue des options d’exécution de requête de SSMS pour définir « XACT_ABORT ». Cette option est activée par défaut dans cette version de SSMS et demande à SQL Server de restaurer l’intégralité de la transaction et d’abandonner le traitement en cas d’erreur d’exécution.

* Prise en charge d’Azure SQL Data Warehouse dans SSMS.

* Mises à jour importantes apportées au module SQL Server PowerShell. Cela inclut un nouveau [module SQL PowerShell et de nouvelles applets de commande pour le chiffrement intégral, SQL Agent et les journaux d’erreurs SQL](https://blogs.technet.microsoft.com/dataplatforminsider/2016/06/30/sql-powershell-july-2016-update).

* Prise en charge de la génération de scripts PowerShell dans l’Assistant Chiffrement intégral.

* Délais de connexion aux bases de données SQL Azure considérablement améliorés.

* Nouvelle boîte de dialogue Backup to URL (Sauvegarde vers l’URL) pour prendre en charge la création d’informations d’identification de stockage Azure pour les sauvegardes de bases de données SQL Server 2016. Cette boîte de dialogue fournit une expérience plus fluide pour stocker les sauvegardes de bases de données dans un compte de stockage Azure.
 
* Nouvelle boîte de dialogue Restore (Restauration) pour simplifier la restauration d’une sauvegarde de base de données SQL Server 2016 à partir du service de stockage Microsoft Azure.
 
* Résolution de bogue dans le concepteur de requêtes SSMS pour autoriser l’ajout de tables au concepteur si un utilisateur ne dispose pas d’autorisations SELECT sur celles-ci.

* Résolution de bogue pour ajouter la prise en charge d’IntelliSense pour les fonctions « TRY_CAST() » et « TRY_CONVERT() ».  
*Demandes de correctif connexes des clients :*  
[Article Microsoft Connect n°2453461](https://connect.microsoft.com/SQLServer/feedback/details/2453461/sql-server-2012-issue-with-try-cast).

* Résolution de bogue dans le module PowerShell pour activer le chargement de l’extension Analysis Services « SQLAS ».  
*Demandes de correctif connexes des clients :*  
[Article Microsoft Connect n°2544902](https://connect.microsoft.com/SQLServer/feedback/details/2544902/ssms-march-2016-refresh-sqlps-failed-to-load-the-sqlas-extension).

* Résolution de bogue dans la fenêtre de l’éditeur de SSMS pour autoriser l’ouverture par glisser-déplacer de fichiers SQL.  
*Demandes de correctif connexes des clients :*  
[Article Microsoft Connect n°2690658](https://connect.microsoft.com/SQLServer/feedback/details/2690658/cannot-drag-sql-files-into-management-studios).

* Résolution de bogue dans Profiler pour résoudre les blocages de Profiler lors de la sortie.  
*Demandes de correctif connexes des clients :*  
[Article Microsoft Connect n°2616550](https://connect.microsoft.com/SQLServer/feedback/details/2616550/sql-server-2016-rc2-profiler-version-13-0-1300-275-wont-close-after-trace-is-started-even-after-trace-is-stopped).  
[Article Microsoft Connect n°2319968](https://connect.microsoft.com/SQLServer/Feedback/Details/2319968).

* Résolution de bogue dans SSMS pour éviter l’incident qui se produit lors d’une tentative de modification d’un lien de jointure dans le Concepteur de tables de SSMS.  
*Demandes de correctif connexes des clients :*  
[Article Microsoft Connect n°2721052](https://connect.microsoft.com/SQLServer/feedback/details/2721052/ssms-view-design-mode-right-click-on-join-crashes-ssms).

* Résolution de bogue dans SSMS pour activer la génération de script de base de données pour les membres du rôle db_owner.  
*Demandes de correctif connexes des clients :*  
[Article Microsoft Connect n°2869241](https://connect.microsoft.com/SQLServer/feedback/details/2869241/error-with-script-database-as-create-to-in-ssms-2008r2-and-ssms-2016-june).

* Résolution de bogue dans l’éditeur de SSMS pour supprimer le délai de fermeture d’un onglet de requête si le serveur a été mis hors connexion.  
*Demandes de correctif connexes des clients :*  
[Article Microsoft Connect n°2656058](https://connect.microsoft.com/SQLServer/feedback/details/2656058/ssms-2014-2016-query-tab-takes-significantly-longer-to-close-if-the-instance-it-was-connected-to-is-now-offline).

* Résolution de bogue pour activer l’option de sauvegarde dans les bases de données SQL Server Express. 
*Demandes de correctif connexes des clients :*  
[Article Microsoft Connect n°2801910](https://connect.microsoft.com/SQLServer/feedback/details/2801910/ssms-2016-backup-option-not-appearing-in-tasks).  
[Article Microsoft Connect n°2874434](https://connect.microsoft.com/SQLServer/feedback/details/2874434/backup-missing-from-tasks-context-menu-in-ssms-2016-when-you-are-connected-to-an-express-instance).

* Résolution de bogue dans Analysis Services pour afficher correctement le fournisseur de flux de données pour les modèles Analysis Services multidimensionnels.

----
## <a name="downloadssdtmediadownloadpng-ssms-june-2016httpgomicrosoftcomfwlinklinkid799832"></a>![télécharger](../ssdt/media/download.png) [SSMS, juin 2016](http://go.microsoft.com/fwlink/?LinkID=799832)
Généralement disponible | Numéro de version : 13.0.15000.23

* SSMS est généralement disponible depuis la version de juin 2016.

* La nouvelle boîte de dialogue Recherche rapide dans SSMS est mieux intégrée dans le document actif, et permet de rechercher des expressions régulières. 
*Demandes de correctif connexes des clients :*  
<https://connect.microsoft.com/SQLServer/feedback/details/2735513/quick-find-replace-in-ssms-2016-rc3/>

* Améliorations du programme d’installation de SSMS permettant de suivre la progression de l’installation et les codes de sortie du processus pour les installations sans assistance à l’aide de scripts.

* Résolution de bogue dans l’aide contextuelle (accessible via la touche F1) de SSMS afin d’afficher correctement les documents et articles d’aide.

* Résolution de bogue dans la vue « Requêtes régressées » du Magasin de données de requête, qui entraînait le blocage de SSMS lors du défilement.

* Résolution de bogue dans le connecteur Analysis Services OLEDB d’Excel pour autoriser les connexions d’Excel 2016 à SQL Server Analysis Services.

* Résolution de bogue dans la boîte de dialogue Connexion de SSMS pour afficher la boîte de dialogue de connexion sur le même moniteur que la fenêtre principale de SSMS dans les systèmes multimoniteur.  
*Demandes de correctif connexes des clients :*  
<https://connect.microsoft.com/SQLServer/feedback/details/724909/connection-dialog-appears-off-screen/>
<https://connect.microsoft.com/SQLServer/feedback/details/755689/sql-server-management-studio-connect-to-server-popup-dialog/>  
<https://connect.microsoft.com/SQLServer/feedback/details/389165/sql-server-management-studio-gets-confused-dealing-with-multiple-displays/>

* Résolution de bogue dans l’expérience Always Encrypted. Résolution du bogue où l’option de menu Always Encrypted n’était pas activée correctement pour les bases de données Stretch. Également résolution du bogue de l’Assistant Always Encrypted qui n’utilisait pas correctement le fournisseur HSM SafeNet (Luna SA).


## <a name="additional-downloads"></a>Téléchargements supplémentaires  
Pour obtenir la liste de tous les téléchargements de SQL Server Management Studio, rechercher dans le [Centre de téléchargement Microsoft](https://www.microsoft.com/en-us/download/search.aspx?q=sql%20server%20management%20studio&p=0&r=10&t=&s=Relevancy~Descending).  
  
Pour obtenir la dernière version de SQL Server Management Studio, voir [Télécharger SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md).  

