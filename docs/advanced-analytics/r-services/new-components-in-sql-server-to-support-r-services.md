---
title: "De nouveaux composants de SQL Server pour prendre en charge les Services de R | Microsoft Docs"
ms.custom: ""
ms.date: "06/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54e9ef3f-1136-471e-865a-7cf013673186
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 9
---
# De nouveaux composants de SQL Server pour prendre en charge les Services de R

[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] inclut de nouveaux composants, fournis par le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] moteur de base de données qui prennent en charge d’extensibilité pour le langage R. La sécurité de ces composants est gérée par [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] et sera abordé en détail ultérieurement.

## Les fournisseurs et les nouveaux composants SQL Server

En plus de l’interpréteur de commandes qui charge R et exécute le code R, comme décrit dans la vue d’ensemble de l’architecture, [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] inclut les composants supplémentaires.

### **LaunchPad** 
  Le [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] est un service fourni par [!INCLUDE[ssCurrent_md](../../includes/sscurrent-md.md)] pour prendre en charge l’exécution des scripts externes, similaires à la façon dont le service d’indexation et de requête de recherche en texte intégral lance un hôte distinct pour le traitement des requêtes de texte intégral. 
  
  Le service Launchpad démarre uniquement les lanceurs approuvés qui sont publiés par Microsoft, ou qui ont été certifiés par Microsoft en tant que demandes de réunion pour la gestion des ressources et des performances. Dans [!INCLUDE[ssCurrent_md](../../includes/sscurrent-md.md)], R est la langue externe uniquement pris en charge par le [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)].
  
  Le [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] service s’exécute sous son propre compte d’utilisateur. Le compte d’utilisateur de la zone de lancement héritera de chaque processus satellite pour un runtime de langage spécifique. Pour plus d’informations sur la configuration et le contexte de sécurité de la zone de lancement, consultez [vue d’ensemble de la sécurité](../../advanced-analytics/r-services/security-overview-sql-server-r-services.md).

### **BxlServer et par Satellite SQL**
  BxlServer est un fichier exécutable fourni par Microsoft qui gère la communication entre [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] et le runtime de R et également implémente les fonctions ScaleR. Il crée les objets de travail Windows qui sont utilisées pour contenir des sessions R, dispositions sécurisé dossiers de travail pour chaque tâche R et utilise SQL Satellite pour gérer le transfert de données entre R et [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].  

  En effet, BxlServer est un complément qui fonctionne avec R [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] pour prendre en charge l’intégration de R avec SQL Server. BXL est l’abréviation de langue des binaires Exchange et fait référence au format de données utilisé pour déplacer efficacement des données entre SQL Server et des processus externes, tels que R. 

 Satellite SQL est une nouvelle API d’extensibilité dans SQL Server 2016 fourni par le moteur de base de données pour prendre en charge le code externe ou externes runtimes implémentés à l’aide de C ou C++. Actuellement, R est le seul runtime pris en charge. BxlServer utilise SQL Satellite pour la communication avec [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
 
  Satellite SQL utilise un format de données personnalisé qui est optimisé pour les transferts de données rapides entre [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] et langages de script externe. Il effectue des conversions de type et définit les schémas des jeux de données d’entrée et de sortie pendant les communications entre [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] et r.

  BxlServer utilise SQL Satellite pour les tâches suivantes : 
  - Lire les données d’entrée
  - Écriture des données de sortie
  - Obtient les arguments d’entrée
  - Écrit les arguments de sortie
  - Gestion des erreurs
  - Réécriture STDOUT et STDERR sur le client

  Satellite SQL peuvent être surveillé à l’aide d’événements étendus. Pour plus d’informations, consultez [événements étendus pour les Services de SQL Server R](../../advanced-analytics/r-services/extended-events-for-sql-server-r-services.md).


## Les canaux de communication entre les composants

+ **TCP/IP** par défaut, les communications internes entre [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] et Satellite SQL utilisent TCP/IP.

+ **Canaux nommés**

  Transport de données interne entre le BxlServer et [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] par Satellite de SQL utilise un format de données propriétaires, compressé pour améliorer les performances. Données de la mémoire de R à BxlServer sont échangées via des canaux nommés au format BXL. 
  
+ **ODBC** Communications entre les clients de science des données externes et les [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] instance utilisent ODBC. Des travaux pour le compte qui envoie la R [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] doit avoir deux autorisations pour se connecter à l’instance et à exécuter des scripts externes. En outre, le compte doit être autorisé à accéder aux données utilisées par la tâche, pour écrire des données (par exemple, si l’enregistrement des résultats dans une table), ou pour créer des objets de base de données (par exemple, si l’enregistrement des fonctions R dans le cadre d’une procédure stockée).

  Lorsque [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] est utilisé comme le contexte de calcul pour un travail R envoyés à partir d’un client distant, et la commande R doit récupérer les données d’une source externe, ODBC est utilisé pour l’écriture différée. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] sera mapper l’identité de l’utilisateur qui émet la commande R à distance à l’identité de l’utilisateur sur l’instance actuelle et exécutez la commande ODBC à l’aide des informations d’identification de l’utilisateur. La chaîne de connexion nécessaire pour effectuer cet appel ODBC est obtenue à partir du code client.
  
  Les appels ODBC supplémentaires peuvent être effectués à l’intérieur du script à l’aide de **RODBC**. RODBC est un package R les plus courants d’accès aux données dans les bases de données relationnelles ; Toutefois, ses performances ne sont généralement plus lente que comparables fournisseurs utilisés par [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. De nombreux scripts R utilisent des appels incorporés aux RODBC comme un moyen de récupérer des jeux de données « secondaire » pour une utilisation dans l’analyse. Par exemple, la procédure stockée qui forme un modèle peut définir une requête SQL pour obtenir les données d’apprentissage d’un modèle, mais utiliser un appel RODBC incorporé pour obtenir d’autres facteurs, pour effectuer des recherches, ou pour obtenir de nouvelles données provenant de sources externes telles que des fichiers texte ou Excel.

  Le code suivant illustre un appel RODBC incorporé dans un script R :
   ~~~~
  library(RODBC);
  connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
  dbhandle <- odbcDriverConnect(connStr)
  OutputDataSet <- sqlQuery(dbhandle, "select * from table_name");
  ~~~~

+ **Autres protocoles** processus devront peut-être travailler dans « blocs » ou de transférer des données à un client à distance peuvent également utiliser le. Format XDF pris en charge par le transfert de données réelles de R. Microsoft est via des objets BLOB codé.

## Interaction des composants

L’architecture des composants décrit ci-dessus a été fourni pour garantir que le code open source R peut travailler « tel quel », tandis que la fourniture considérablement améliorer les performances pour le code qui s’exécute sur un [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ordinateur. Le mécanisme de la façon dont les composants interagissent avec le runtime de R et [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] moteur de base de données diffère quelque peu, selon la façon dont le code R est lancé. Les principaux scénarios sont résumées dans cette section. 
 
### Scripts R exécutés à partir de SQL Server (de base de données)

Le code R exécuté à partir de « intérieur » [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] est exécutée en appelant une procédure stockée. Par conséquent, toute application qui peut appeler une procédure stockée peut initier l’exécution de code R.  Par la suite [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] gère l’exécution du code R comme indiqué dans le diagramme suivant.

![rsql_indb780-01](../../advanced-analytics/r-services/media/rsql-indb780-01.png)

1. Une demande pour l’exécution de R est indiquée par le paramètre _@language = 'R'_ transmis à la procédure stockée, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] envoie cette demande au service Launchpad.
2. Le service Launchpad démarre le service de lancement appropriée ; Dans ce cas, RLauncher.
3. RLauncher démarre le processus de R externe.
4. Coordonnées BxlServer avec le runtime R pour gérer les échanges de données avec [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] et le stockage des résultats du travail.
5. Globale, SQL Satellite gère les communications sur les tâches associées et les traite avec [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
6. BxlServer utilise SQL Satellite pour communiquer l’état et les résultats vers [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
7. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Obtient les résultats et ferme les processus et les tâches connexes. 


### Scripts R exécutés à partir d’un client distant

Lors de la connexion d’un client de science des données distantes qui prend en charge Microsoft R, vous pouvez exécuter les fonctions R dans le contexte de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] en utilisant les fonctions ScaleR. Cela est un autre flux de travail de la précédente et est résumée dans le diagramme suivant.


![rsql_fromR2db-01](../../advanced-analytics/r-services/media/rsql-fromr2db-01.png)

1. Pour les fonctions ScaleR, le runtime R appelle une fonction de liaison qui à son tour appelle BxlServer. 
2. BxlServer est fourni avec Microsoft R et s’exécute dans un processus distinct de l’exécution de R.
3. BxlServer détermine la cible de la connexion et initie une connexion à l’aide d’ODBC, en passant les informations d’identification fournies dans le cadre de la chaîne de connexion dans l’objet de source de données R.
4. BxlServer ouvre une connexion à la [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] instance.
5. Pour un appel R, LaunchPad service est appelé, qui est activé démarre le service de lancement approprié, RLauncher. Par la suite, le traitement de code R est semblable au processus d’exécution de code R à partir de T-SQL.
6. RLauncher effectue un appel à l’instance de l’exécution de R est installée sur le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ordinateur. 
7. Les résultats à BxlServer.
8. Gère la communication avec SQL satellites [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] et le nettoyage des objets de traitement connexes.
9. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] transmet les résultats au client.

## Voir aussi
[Vue d'ensemble de l'architecture](../../advanced-analytics/r-services/architecture-overview-sql-server-r-services.md)
