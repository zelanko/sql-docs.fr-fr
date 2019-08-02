---
title: Architecture d’extensibilité pour le langage R et le script Python
description: Prise en charge du code externe pour le moteur de base de données SQL Server, avec une architecture double pour l’exécution de scripts R et Python sur des données relationnelles.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 49c45fa39cd271140ba78c2b1b32ee8a2f9c1a7a
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715255"
---
# <a name="extensibility-architecture-in-sql-server-machine-learning-services"></a>Architecture d’extensibilité dans SQL Server Machine Learning Services 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server a un Framework d’extensibilité pour l’exécution de scripts externes tels que R ou python sur le serveur. Le script s’exécute dans un environnement de Runtime de langage en tant qu’extension du moteur de base de données principal. 

## <a name="background"></a>Présentation

L’infrastructure d’extensibilité a été introduite dans SQL Server 2016 pour prendre en charge le runtime R. SQL Server 2017 et versions ultérieures prennent en charge Python.

L’objectif de l’infrastructure d’extensibilité est de fournir une interface entre les SQL Server et les langages de science des données tels que R et Python, ce qui réduit la friction lors du déplacement des solutions de science des données en production et la protection des données exposées pendant le développement traiter. En exécutant un langage de script approuvé au sein d’une infrastructure sécurisée gérée par SQL Server, les administrateurs de base de données peuvent maintenir la sécurité tout en autorisant l’accès des scientifiques des données aux données d’entreprise.

Le diagramme suivant décrit visuellement les opportunités et les avantages de l’architecture extensible.

  ![Objectifs de l’intégration avec SQL Server](../media/ml-service-value-add.png "Ajout de la valeur machine learning services")

Tout script R ou python peut être exécuté en appelant une procédure stockée, et les résultats sont retournés en tant que résultats tabulaires directement à SQL Server, ce qui facilite la génération ou la consommation des Machine Learning à partir de toute application pouvant envoyer une requête SQL et gérer les résultats.

+ L’exécution du script externe est sujette à SQL Server la sécurité des données, où un utilisateur qui exécute un script externe peut uniquement accéder aux données qui sont également disponibles dans une requête SQL. Si une requête échoue en raison d’une autorisation insuffisante, l’exécution du script par le même utilisateur échoue également pour la même raison. SQL Server la sécurité est appliquée au niveau de la table, de la base de données et de l’instance. Les administrateurs de base de données peuvent gérer l’accès utilisateur, les ressources utilisées par les scripts externes et les bibliothèques de code externes ajoutées au serveur.  

+ Les opportunités de mise à l’échelle et d’optimisation ont une base double: bénéficient de la plate-forme de base de données (index ColumnStore, [gouvernance des ressources](../../advanced-analytics/r/resource-governance-for-r-services.md)) et des gains spécifiques à l’extension lorsque les bibliothèques Microsoft pour R et Python sont utilisées pour les modèles de science des données. Alors que R est monothread, les fonctions RevoScaleR sont multithread et peuvent distribuer une charge de travail sur plusieurs cœurs.

+ Le déploiement utilise des méthodologies de SQL Server: des procédures stockées encapsulant des scripts externes, des requêtes Embedded SQL ou T-SQL appelant des fonctions comme PREDICT pour retourner des résultats à partir de modèles de prévision conservés sur le serveur.

+ Les développeurs R et Python ayant des compétences établies dans des outils et des IDE spécifiques peuvent écrire du code dans ces outils, puis porter le code vers SQL Server.

## <a name="architecture-diagram"></a>Diagramme de l’architecture

L’architecture est conçue de manière à ce que les scripts externes s’exécutent dans un processus distinct de SQL Server, mais avec des composants qui gèrent en interne la chaîne des demandes de données et d’opérations sur SQL Server. Selon la version de SQL Server, les extensions de langage prises en charge incluent R et Python. 

  ![Architecture des composants](../media/generic-architecture.png "Architecture des composants")

Les composants incluent un service **Launchpad** utilisé pour appeler des lanceurs spécifiques à une langue (R ou python), une logique spécifique au langage et à la bibliothèque pour charger des interpréteurs et des bibliothèques. Le lanceur charge une exécution de langage, ainsi que tous les modules propriétaires. Par exemple, si votre code comprend des fonctions RevoScaleR, un interpréteur RevoScaleR se chargera. **BxlServer** et **SQL satellite** gèrent la communication et le transfert de données avec SQL Server.

<a name="launchpad"></a>

## <a name="launchpad"></a>Launchpad

Le [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] est un service qui gère et exécute des scripts externes, de la même façon que le service d’indexation et de recherche en texte intégral lance un hôte distinct pour le traitement des requêtes de texte intégral. Le service Launchpad peut démarrer uniquement les lanceurs approuvés publiés par Microsoft, ou qui ont été certifiés par Microsoft comme exigences en matière de performances et de gestion des ressources.

| Lanceurs approuvés | Extension | Versions de SQL Server |
|-------------------|-----------|---------------------|
| RLauncher. dll pour le langage R | [Extension R](extension-r.md) | SQL Server 2016 et versions ultérieures |
| Pythonlauncher. dll pour Python 3,5 | [Extension Python](extension-python.md) | SQL Server 2017 et versions ultérieures |

Le service [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] s’exécute sous son propre compte d’utilisateur. Si vous modifiez le compte qui exécute Launchpad, veillez à utiliser Gestionnaire de configuration SQL Server pour vous assurer que les modifications sont écrites dans les fichiers associés.

Un service [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] distinct est créé pour chaque instance du moteur de base de données à laquelle vous avez ajouté SQL Server machine learning services. Il existe un service Launchpad pour chaque instance du moteur de base de données. par conséquent, si vous avez plusieurs instances avec prise en charge des scripts externes, vous disposerez d’un service Launchpad pour chacun d’eux. Une instance du moteur de base de données est liée au service Launchpad créé pour celle-ci. Tous les appels de script externe dans une procédure stockée ou un résultat T-SQL dans le service SQL Server appelant le service Launchpad créé pour la même instance.

Pour exécuter des tâches dans une langue spécifique prise en charge, le Launchpad obtient un compte de travail sécurisé à partir du pool et démarre un processus satellite pour gérer le runtime externe. Chaque processus satellite hérite du compte d’utilisateur du Launchpad et utilise ce compte de travail pour la durée de l’exécution du script. Si le script utilise des processus parallèles, ceux-ci sont créés sous le même compte Worker unique.

## <a name="bxlserver-and-sql-satellite"></a>BxlServer et SQL satellites

**BxlServer** est un fichier exécutable fourni par Microsoft qui gère la communication entre SQL Server et Python ou R. Il crée les objets de tâche Windows qui sont utilisés pour contenir des sessions de script externes, configure des dossiers de travail sécurisés pour chaque travail de script externe et utilise SQL satellite pour gérer le transfert de données entre le runtime externe et les SQL Server. Si vous exécutez l' [Explorateur de processus](https://technet.microsoft.com/sysinternals/processexplorer.aspx) pendant l’exécution d’un travail, vous pouvez voir une ou plusieurs instances de BxlServer.

En effet, BxlServer est un complément à un environnement d’exécution de langage qui fonctionne avec SQL Server pour transférer des données et gérer des tâches. BXL correspond au langage d’échange binaire et fait référence au format de données utilisé pour déplacer efficacement les données entre les SQL Server et les processus externes. BxlServer est également une partie importante des produits associés tels que Microsoft R Client et Microsoft R Server.

**SQL satellite** est une API d’extensibilité, incluse dans le moteur de base de données, qui prend en charge le code externe ou C++les runtimes externes implémentés à l’aide de C ou.

BxlServer utilise SQL Satellite pour les tâches suivantes :

+ Lecture des données d’entrée
+ Écriture des données de sortie
+ Obtention des arguments d’entrée
+ Écriture des arguments de sortie
+ Gestion des erreurs
+ Réécriture de STDOUT et de STDERR sur le client

SQL satellite utilise un format de données personnalisé qui est optimisé pour un transfert de données rapide entre des SQL Server et des langages de script externes. Il effectue des conversions de type et définit les schémas des jeux de données d’entrée et de sortie pendant les communications entre SQL Server et le runtime de script externe.

Le satellite SQL peut être surveillé à l’aide des événements étendus Windows (xEvents). Pour plus d’informations, consultez [événements étendus pour R](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md) et les [événements étendus pour Python](../../advanced-analytics/python/extended-events-for-python.md).

## <a name="communication-channels-between-components"></a>Canaux de communication entre les composants

Les protocoles de communication entre les composants et les plateformes de données sont décrits dans cette section.

+ **TCP/IP**

  Par défaut, les communications internes entre SQL Server et le satellite SQL utilisent TCP/IP.

+ **Canaux nommés**

  Le transport de données internes entre BxlServer et SQL Server via SQL satellite utilise un format de données propriétaire et compressé pour améliorer les performances. Les données sont échangées entre les temps d’exécution de langage et les BxlServer au format BXL, à l’aide de canaux nommés.

+ **ODBC**

  Les communications entre les clients de science des données externes et une instance de SQL Server distante utilisent ODBC. Le compte qui envoie les travaux de script à SQL Server doit disposer des autorisations pour se connecter à l’instance et pour exécuter des scripts externes.

  En outre, en fonction de la tâche, le compte peut avoir besoin des autorisations suivantes:

  + Lire les données utilisées par le travail
  + Écrire des données dans des tables: par exemple, lors de l’enregistrement des résultats dans une table
  + Créer des objets de base de données: par exemple, si vous enregistrez un script externe dans le cadre d’une nouvelle procédure stockée.

  Lorsque SQL Server est utilisé comme contexte de calcul pour un script exécuté à partir d’un client distant, et que l’exécutable doit extraire des données d’une source externe, ODBC est utilisé pour l’écriture différée. SQL Server mappe l’identité de l’utilisateur qui émet la commande à distance à l’identité de l’utilisateur sur l’instance actuelle, puis exécute la commande ODBC à l’aide des informations d’identification de cet utilisateur. La chaîne de connexion nécessaire pour effectuer cet appel ODBC est obtenue à partir du code client.

+ **RODBC (R uniquement)** 

  Des appels ODBC supplémentaires peuvent être effectués à l’intérieur du script à l’aide du package **RODBC**. RODBC est un package R populaire utilisé pour accéder aux données dans les bases de données relationnelles. Toutefois, ses performances sont généralement plus lentes que les fournisseurs comparables utilisés par SQL Server. De nombreux scripts R utilisent des appels au RODBC incorporés comme moyen de récupérer les jeux de données « secondaires » à utiliser dans les analyses. Par exemple, la procédure stockée qui forme un modèle peut définir une requête SQL pour obtenir les données d’apprentissage d’un modèle, mais utiliser un appel RODBC incorporé pour obtenir d’autres facteurs, effectuer des recherches ou obtenir de nouvelles données de sources externes telles que des fichiers texte ou Excel.

  Le code suivant illustre un appel RODBC incorporé dans un script R :

    ```R
    library(RODBC);
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    dbhandle <- odbcDriverConnect(connStr)
    OutputDataSet <- sqlQuery(dbhandle, "select * from table_name");
    ```

+ **Autres protocoles**

  Les processus qui peuvent avoir besoin de travailler dans des «segments» ou de transférer des données vers un client distant peuvent également utiliser le [format de fichier XDF](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf). Le transfert de données réel s’effectue par le biais d’objets BLOB encodés.

## <a name="see-also"></a>Voir aussi

+ [Extension R dans SQL Server](extension-r.md)
+ [Extension Python dans SQL Server](extension-python.md)