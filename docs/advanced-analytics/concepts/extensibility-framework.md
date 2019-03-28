---
title: Architecture d’extensibilité pour le langage R et SQL Server Machine Learning - le script Python
description: Le code externe prise en charge pour le moteur de base de données SQL Server, avec une architecture double pour l’exécution de script R et Python sur des données relationnelles.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 8e5f874e43e70ce1bddfe21b745199fef44aa04a
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510626"
---
# <a name="extensibility-architecture-in-sql-server-machine-learning-services"></a>Architecture d’extensibilité dans SQL Server Machine Learning Services 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server dispose d’une infrastructure d’extensibilité pour l’exécution de script externe comme R ou Python sur le serveur. Script s’exécute dans un environnement d’exécution de langage en tant qu’extension du moteur de base de données principal. 

## <a name="background"></a>Arrière-plan

L’infrastructure d’extensibilité a été introduite dans SQL Server 2016 pour prendre en charge le runtime R. SQL Server 2017 ajoute la prise en charge de Python

L’objectif de l’infrastructure d’extensibilité consiste à fournir une interface entre SQL Server et les langues de science des données tels que R et Python, réduisant les frictions lorsque des solutions de science des données mobiles en production et à protéger les données exposées lors du développement processus. En exécutant un langage de script approuvé au sein d’une infrastructure sécurisée géré par SQL Server, les administrateurs de base de données peuvent maintenir la sécurité tout en permettant aux scientifiques des données de l’accès aux données d’entreprise.

Le diagramme suivant décrit visuellement les opportunités et les avantages de l’architecture extensible.

  ![Objectifs de l’intégration avec SQL Server](../media/ml-service-value-add.png "Machine Learning Services à valeur ajoutée")

N’importe quel script R ou Python peut être exécuté en appelant une procédure stockée, et les résultats sont retournés en tant que résultats tabulaires directement à SQL Server, ce qui facilite générer ou consommer d’apprentissage à partir de n’importe quelle application qui peut envoyer une requête SQL et gérer les résultats.

+ L’exécution du script externe est exposée à la sécurité de données SQL Server, où un utilisateur exécute le script externe peut uniquement accéder aux données qui est également disponible dans une requête SQL. Si une requête échoue en raison d’une autorisation insuffisante, le script exécuté par le même utilisateur échoue également pour la même raison. Sécurité de SQL Server est appliquée à la table, la base de données et le niveau de l’instance. Les administrateurs de base de données peuvent gérer des accès utilisateur, les ressources utilisées par les scripts externes et les bibliothèques de code externe ajoutés au serveur.  

+ Mise à l’échelle et l’optimisation des opportunités disposer d’une base double : gains via la plateforme de base de données (index ColumnStore, [gouvernance des ressources](../../advanced-analytics/r/resource-governance-for-r-services.md)) et des avantages en matière de spécifiques à l’extension des bibliothèques de Microsoft pour R et Python sont utilisés pour les données modèles de science. Alors que R est monothread, les fonctions RevoScaleR sont multithreads et capable de distribution d’une charge de travail sur plusieurs cœurs.

+ Déploiement utilise les méthodologies de SQL Server : procédures stockées d’habillage de scripts externes, embedded SQL, ou T-SQL interroge appeler des fonctions telles que PREDICT pour retourner les résultats à partir de modèles de prévision conservés sur le serveur.

+ Les développeurs R et Python avec établie compétences dans les outils spécifiques et différents IDE peuvent écrire du code dans ces outils et ensuite le portage de code pour SQL Server.

## <a name="architecture-diagram"></a>Diagramme de l'architecture

L’architecture est conçue de telle sorte que les scripts externes exécutés dans un processus séparé à partir de SQL Server, mais avec des composants qui gèrent en interne la chaîne de demandes de données et les opérations sur SQL Server. Selon la version de SQL Server, les extensions de langage pris en charge incluent R et Python. 

  ![Architecture du composant](../media/generic-architecture.png "architecture du composant")

Composants incluent un **Launchpad** utilisée pour appeler le langage (R ou Python), de lanceurs de spécifique à la langue et logique de bibliothèque spécifique pour le chargement des interpréteurs et bibliothèques de service. Le Lanceur charge un temps de langage exécuter, ainsi que tous les modules propriétaires. Par exemple, si votre code inclut les fonctions RevoScaleR, un interpréteur RevoScaleR chargerait. **BxlServer** et **SQL Satellite** gérer les transferts de communications et les données avec SQL Server.

<a name="launchpad"></a>

## <a name="launchpad"></a>Launchpad

Le [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] est un service qui gère et exécute des scripts externes, similaires à la façon dont le service d’indexation et de requête de recherche en texte intégral lance un hôte distinct pour le traitement des requêtes de recherche en texte intégral. Le service Launchpad peut démarrer uniquement les lanceurs approuvés qui sont publiés par Microsoft, ou qui ont été certifiés par Microsoft comme répondant aux exigences pour la gestion des ressources et des performances.

| Lanceurs approuvés | Extension | Versions de SQL Server |
|-------------------|-----------|---------------------|
| RLauncher.dll pour le langage R | [Extension de R](extension-r.md) | SQL Server 2016, SQL Server 2017 |
| Pythonlauncher.dll pour Python 3.5 | [Extension Python](extension-python.md) | SQL Server 2017 |

Le service [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] s’exécute sous son propre compte d’utilisateur. Si vous modifiez le compte qui exécute Launchpad, veillez à le faire à l’aide du Gestionnaire de Configuration SQL Server pour vous assurer que les modifications sont écrites dans les fichiers associés.

Distinct [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] service est créé pour chaque instance du moteur de base de données à laquelle vous avez ajouté SQL Server Machine Learning Services. Il existe un Launchpad service pour chaque instance du moteur de base de données, donc si vous avez plusieurs instances avec prise en charge de script externe, vous aura un service Launchpad pour chacun d'entre eux. Une instance du moteur de base de données est liée au service Launchpad créé pour lui. Tous les appels de script externe dans une procédure stockée ou un résultat de T-SQL dans le service SQL Server d’appeler le service Launchpad créé pour la même instance.

Pour exécuter des tâches dans une langue prise en charge spécifique, le Launchpad Obtient un compte de travail sécurisé à partir du pool et démarre un processus satellite pour gérer le runtime externe. Chaque processus satellite hérite le compte d’utilisateur de Launchpad et utilise ce compte de travail pendant la durée de l’exécution du script. Si le script utilise les traitements parallèles, ils sont créés sous le compte de travail de même, unique.

## <a name="bxlserver-and-sql-satellite"></a>BxlServer et SQL Satellite

**BxlServer** est un fichier exécutable fourni par Microsoft qui gère la communication entre SQL Server et Python ou R. Il crée les objets de travail de Windows qui sont utilisés pour contenir les sessions de script externe, dispositions sécurisé dossiers de travail pour chaque tâche de script externe et utilise SQL Satellite pour gérer les transferts de données entre le runtime externe et SQL Server. Si vous exécutez [Process Explorer](https://technet.microsoft.com/sysinternals/processexplorer.aspx) pendant l’exécution d’un travail, vous pouvez voir une ou plusieurs instances de BxlServer.

En effet, BxlServer est un complément à un environnement d’exécution qui fonctionne avec SQL Server pour transférer des données et de gérer les tâches de langage. BXL signifie Binary Exchange language et fait référence au format de données utilisé pour déplacer efficacement des données entre SQL Server et des processus externes. BxlServer est également une partie importante de produits connexes tels que Microsoft R Client et Microsoft R Server.

**SQL Satellite** est une API d’extensibilité, inclus dans le moteur de base de données en commençant par SQL Server 2016, qui prend en charge le code externe ou les runtimes externes implémentés à l’aide de C ou C++.

BxlServer utilise SQL Satellite pour les tâches suivantes :

+ Lecture des données d’entrée
+ Écriture des données de sortie
+ Obtention des arguments d’entrée
+ Écriture des arguments de sortie
+ Gestion des erreurs
+ Réécriture de STDOUT et de STDERR sur le client

SQL Satellite utilise un format de données personnalisé qui est optimisé pour le transfert de données rapides entre SQL Server et les langages de script externe. Il effectue des conversions de type et définit les schémas des jeux de données d’entrée et de sortie pendant les communications entre SQL Server et le runtime de script externe.

SQL Satellite peut être surveillé à l’aide de windows (xEvents) d’événements étendus. Pour plus d’informations, consultez [événements étendus pour R](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md) et [événements étendus pour Python](../../advanced-analytics/python/extended-events-for-python.md).

## <a name="communication-channels-between-components"></a>Canaux de communication entre les composants

Protocoles de communication entre les composants et les plateformes de données sont décrits dans cette section.

+ **TCP/IP**

  Par défaut, les communications internes entre SQL Server et SQL Satellite utilisent TCP/IP.

+ **Canaux nommés**

  Transport des données internes entre BxlServer et de SQL Server via SQL Satellite utilise un format de données propriétaire et compressé pour améliorer les performances. Au format BXL, à l’aide de canaux nommés, les données sont échangées entre les heures de langage exécuter et BxlServer.

+ **ODBC**

  Communications entre les clients de science des données externes et une instance distante de SQL Server utilisent ODBC. Le compte qui envoie les tâches de script à SQL Server doit avoir deux autorisations pour se connecter à l’instance et d’exécuter des scripts externes.

  En outre, selon la tâche, le compte peut-être besoin de ces autorisations :

  + Lire les données utilisées par le travail
  + Écrire des données dans les tables : par exemple, lorsque l’enregistrement des résultats dans une table
  + Créer des objets de base de données : par exemple, si l’enregistrement de script externe dans le cadre d’une nouvelle procédure stockée.

  Lorsque SQL Server est utilisé comme contexte de calcul pour le script exécuté à partir d’un client distant et le fichier exécutable doivent récupérer des données à partir d’une source externe, ODBC est utilisé pour l’écriture différée. SQL Server mappe l’identité de l’utilisateur qui émet la commande à distance à l’identité de l’utilisateur sur l’instance actuelle et exécute la commande ODBC à l’aide des informations d’identification de cet utilisateur. La chaîne de connexion nécessaire pour effectuer cet appel ODBC est obtenue à partir du code client.

+ **RODBC (R uniquement)** 

  Des appels ODBC supplémentaires peuvent être effectués à l’intérieur du script à l’aide du package **RODBC**. RODBC est un package R couramment utilisé pour accéder aux données dans les bases de données relationnelles ; Toutefois, ses performances sont généralement plus lent que les fournisseurs comparables utilisés par SQL Server. De nombreux scripts R utilisent des appels au RODBC incorporés comme moyen de récupérer les jeux de données « secondaires » à utiliser dans les analyses. Par exemple, la procédure stockée qui forme un modèle peut définir une requête SQL pour obtenir les données d’apprentissage d’un modèle, mais utiliser un appel RODBC incorporé pour obtenir d’autres facteurs, effectuer des recherches ou obtenir de nouvelles données de sources externes telles que des fichiers texte ou Excel.

  Le code suivant illustre un appel RODBC incorporé dans un script R :

    ```R
    library(RODBC);
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    dbhandle <- odbcDriverConnect(connStr)
    OutputDataSet <- sqlQuery(dbhandle, "select * from table_name");
    ```

+ **Autres protocoles**

  Processus qui devront peut-être travailler dans « blocs » ou transférer des données à un client à distance peuvent également utiliser le [format de fichier XDF](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf). Transfert de données réelles est via des objets BLOB encodés.

## <a name="see-also"></a>Voir aussi

+ [Extension de R dans SQL Server](extension-r.md)
+ [Extension de Python dans SQL Server](extension-python.md)