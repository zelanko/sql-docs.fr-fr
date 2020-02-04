---
title: Architecture d’extensibilité
description: Cet article décrit l’architecture du framework d’extensibilité pour l’exécution d’un script externe (p.ex., en R ou Python) sur un serveur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/04/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: fcdb92f92ffb8239a6cf20b0f39dfb8f546b521a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "73727690"
---
# <a name="extensibility-architecture-in-sql-server-machine-learning-services"></a>Architecture d’extensibilité dans SQL Server Machine Learning Services 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server est doté d’un framework d’extensibilité pour l’exécution d’un script externe (p.ex., en R ou Python) sur le serveur. Le script s’exécute dans un environnement de runtime de langage en tant qu’extension du moteur de base de données de base.

## <a name="background"></a>Arrière-plan

Le framework d’extensibilité a été introduit dans SQL Server 2016 pour prendre en charge le runtime R. SQL Server 2017 et les versions ultérieures prennent en charge Python.

Le framework d’extensibilité vise à offrir une interface entre SQL Server et les langages de science des données comme R et Python. L’objectif est de réduire la friction pendant le déplacement de solutions de science des données en production et quand il s’agit de protéger les données exposées durant le processus de développement. L’exécution d’un langage de script approuvé au sein d’un framework sécurisé et gérée par SQL Server permet aux administrateurs de base de données d’assurer la sécurité tout en permettant aux scientifiques des données d’accéder aux données de l’entreprise.

Le schéma suivant décrit visuellement les possibilités et les avantages de l’architecture extensible.

  ![Objectifs de l’intégration avec SQL Server](../media/ml-service-value-add.png "Valeur ajoutée de Machine Learning Services")

Il est possible d’exécuter un script externe en appelant une procédure stockée ; les résultats sont alors directement retournés sous forme tabulaire à SQL Server. Cela facilite la génération ou l’utilisation du Machine Learning à partir de n’importe quelle application capable d’envoyer une requête SQL et de gérer les résultats.

+ L’exécution d’un script externe est soumise aux règles de sécurité des données de SQL Server. Un utilisateur exécutant un script externe peut uniquement accéder aux données qui sont également disponibles dans une requête SQL. Si une requête échoue en raison d’autorisations insuffisantes, un script exécuté par le même utilisateur échouera aussi pour la même raison. La sécurité de SQL Server est appliquée au niveau de la table, de la base de données et de l’instance. Les administrateurs de base de données peuvent gérer l’accès des utilisateurs, les ressources utilisées par les scripts externes et les bibliothèques de code externes ajoutées au serveur.  

+ Les possibilités de mise à l’échelle et d’optimisation reposent sur deux piliers : avantages liés à la plateforme de base de données (index ColumnStore, [gouvernance des ressources](../../advanced-analytics/r/resource-governance-for-r-services.md)) et avantages propres à l’extension, par exemple quand les bibliothèques Microsoft pour R et Python sont utilisées pour les modèles de science des données. Si R est monothread, les fonctions RevoScaleR sont en revanche multithread et capables de répartir une charge de travail entre plusieurs cœurs.

+ Le déploiement s’appuie sur les méthodologies SQL Server. Il peut s’agir de procédures stockées encapsulant un script externe, des requêtes SQL ou T-SQL incorporées appelant des fonctions comme PREDICT pour retourner des résultats à partir de modèles de prévision conservés sur le serveur.

+ Les développeurs qui maîtrisent des outils et IDE spécifiques peuvent écrire du code dans ces outils, puis porter ce code sur SQL Server.

## <a name="architecture-diagram"></a>Diagramme de l'architecture

L’architecture est conçue de telle sorte que les scripts externes s’exécutent dans un processus distinct de SQL Server, mais avec des composants qui gèrent en interne la chaîne des demandes de données et d’opérations dans SQL Server. Selon la version de SQL Server, les extensions de langage prises en charge incluent [R](extension-r.md), [Python](extension-python.md) et des langages tiers comme Java et .NET.

  ***Architecture des composants dans Windows :***
  
  ![Architecture des composants Windows](../media/generic-architecture-windows.png "Architecture des composants")
  
  ***Architecture des composants dans Linux :***

  ![Architecture des composants Linux](../media/generic-architecture-linux.png "Architecture des composants")
  
Parmi les composants figurent un service **launchpad** destiné à appeler des runtimes externes et une logique spécifique de bibliothèque pour charger interpréteurs et autres bibliothèques. Le lanceur charge un runtime de langage ainsi que les modules propriétaires éventuels. Par exemple, si votre code comprend des fonctions RevoScaleR, un interpréteur RevoScaleR est chargé. **BxlServer** et **SQL Satellite** gèrent la communication et le transfert de données avec SQL Server. 

Dans Linux, SQL utilise un service **launchpad** pour communiquer avec un processus launchpad distinct pour chaque utilisateur.

<a name="launchpad"></a>

## <a name="launchpad"></a>Launchpad

[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] est un service qui gère et exécute les scripts externes, à l’image du service de requête et d’indexation de texte intégral qui lance un hôte distinct pour le traitement de requêtes de texte intégral. Le service launchpad peut démarrer uniquement les lanceurs approuvés et publiés par Microsoft ou qui ont été certifiés par Microsoft comme répondant aux exigences de performances et de gestion des ressources.

| Lanceurs approuvés | Extension | Versions de SQL Server |
|-------------------|-----------|---------------------|
| RLauncher. dll pour le langage R pour Windows | [Extension R](extension-r.md) | SQL Server 2016 et versions ultérieures |
| Pythonlauncher.dll pour Python 3.5 pour Windows | [Extension Python](extension-python.md) | SQL Server 2017 et versions ultérieures |
| RLauncher.so pour le langage R pour Linux | [Extension R](extension-r.md) | SQL Server 2019 et versions ultérieures |
| Pythonlauncher.so for Python 3.5 pour Linux | [Extension Python](extension-python.md) | SQL Server 2019 et versions ultérieures |

Le service [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] s’exécute sous son propre compte d’utilisateur. Si vous modifiez le compte qui exécute launchpad, veillez à utiliser le Gestionnaire de configuration SQL Server pour faire en sorte que les modifications soient écrites dans les fichiers associés.

Dans Windows, un service [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] distinct est créé pour chaque instance de moteur de base de données à laquelle vous avez ajouté SQL Server Machine Learning Services. Il existe un service launchpad pour chaque instance de moteur de base de données. Par conséquent, si vous avez plusieurs instances avec prise en charge des scripts externes, vous aurez un service launchpad pour chacune d’elles. Une instance de moteur de base de données est liée au service launchpad qui a été créé pour celle-ci. Pour tous les appels de script externe d’une procédure stockée ou de T-SQL, le service SQL Server appelle le service launchpad créé pour la même instance.

Pour exécuter des tâches dans un langage spécifique pris en charge, le service launchpad obtient un compte de travail sécurisé auprès du pool, puis démarre un processus satellite pour gérer le runtime externe. Chaque processus satellite hérite du compte d’utilisateur du service launchpad et utilise ce compte de travail pendant la durée d’exécution du script. Si le script utilise des processus parallèles, ils sont créés sous le même compte Worker unique.

Dans Linux, une seule instance de moteur de base de données est prise en charge et un seul service launchpad est lié à l’instance. Quand un script est exécuté, le service launchpad lance un processus launchpad distinct avec le compte d’utilisateur à faibles privilèges **mssql_satellite**. Chaque processus satellite hérite du compte d’utilisateur mssql_satellite du service launchpad et l’utilise pendant la durée d’exécution du script.

## <a name="bxlserver-and-sql-satellite"></a>BxlServer et SQL Satellite

**BxlServer** est un exécutable fourni par Microsoft qui gère la communication entre SQL Server et le runtime de langage. Il crée les objets de traitement Windows pour Windows, ou les espaces de noms pour Linux, qui servent à accueillir les sessions de script externe. De même, il provisionne des dossiers de travail sécurisés pour chaque travail de script externe et utilise SQL Satellite pour gérer le transfert de données entre le runtime externe et SQL Server. Si vous exécutez l’[Explorateur de processus](https://technet.microsoft.com/sysinternals/processexplorer.aspx) pendant l’exécution d’un travail, vous pouvez noter la présence d’une ou plusieurs instances de BxlServer.

En effet, BxlServer est un complément d’environnement de runtime de langage qui fonctionne avec SQL Server pour transférer les données et gérer les tâches. BXL, qui est l’abréviation de « Binary Exchange Language », désigne le format de données utilisé pour déplacer efficacement les données entre SQL Server et les processus externes. BxlServer est aussi une composante importante de produits associés comme Microsoft R Client et Microsoft R Server.

**SQL Satellite** est une API d’extensibilité intégrée dans le moteur de base de données qui prend en charge le code ou les runtimes externes implémentés en C ou C++.

BxlServer utilise SQL Satellite pour les tâches suivantes :

+ Lecture des données d’entrée
+ Écriture des données de sortie
+ Obtention des arguments d’entrée
+ Écriture des arguments de sortie
+ Gestion des erreurs
+ Réécriture de STDOUT et de STDERR sur le client

SQL Satellite utilise un format de données personnalisé qui est optimisé pour accélérer les transferts de données entre SQL Server et les langages de script externe. Il assure les conversions de type et définit les schémas des jeux de données d’entrée et de sortie pendant les communications entre SQL Server et le runtime de script externe.

SQL Satellite peut être supervisé en utilisant des événements étendus Windows (xEvents). Pour plus d’informations, consultez [Événements étendus pour R](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md) et [Événements étendus pour Python](../../advanced-analytics/python/extended-events-for-python.md).

## <a name="communication-channels-between-components"></a>Canaux de communication entre les composants

Les protocoles de communication entre les composants et les plateformes de données sont décrits dans cette section.

+ **TCP/IP**

  Par défaut, les communications internes entre SQL Server et SQL Satellite utilisent TCP/IP.

+ **Canaux nommés**

  Le transport de données interne entre BxlServer et SQL Server via SQL Satellite utilise un format de données propriétaire et compressé pour améliorer les performances. Les données sont échangées entre les runtimes de langage et BxlServer au format BXL, en utilisant les canaux nommés.

+ **ODBC**

  Les communications entre les clients de science des données externes et une instance de SQL Server distante utilisent ODBC. Le compte qui envoie les travaux de script à SQL Server doit avoir l’autorisation de se connecter à l’instance et l’autorisation d’exécuter des scripts externes.

  De plus, en fonction de la tâche, le compte peut avoir besoin des autorisations suivantes :

  + Lire les données utilisées par le travail
  + Écrire les données dans des tables : par exemple, durant l’enregistrement des résultats dans une table
  + Créer des objets de base de données : par exemple, si vous enregistrez un script externe dans le cadre d’une nouvelle procédure stockée

  Quand SQL Server sert de contexte de calcul pour un script exécuté à partir d’un client distant et que l’exécutable doit récupérer des données à partir d’une source externe, ODBC est utilisé pour l’écriture différée. SQL Server mappe l’identité de l’utilisateur qui émet la commande distante à l’identité de l’utilisateur sur l’instance actuelle, puis exécute la commande ODBC à l’aide des informations d’identification de cet utilisateur. La chaîne de connexion nécessaire pour effectuer cet appel ODBC est obtenue à partir du code client.

+ **RODBC (R uniquement)** 

  Des appels ODBC supplémentaires peuvent être effectués à l’intérieur du script à l’aide du package **RODBC**. RODBC est un package R couramment utilisé pour accéder aux données de bases de données relationnelles. Cependant, il est généralement moins rapide que les fournisseurs comparables utilisés par SQL Server. De nombreux scripts R utilisent des appels au RODBC incorporés comme moyen de récupérer les jeux de données « secondaires » à utiliser dans les analyses. Par exemple, la procédure stockée qui forme un modèle peut définir une requête SQL pour obtenir les données d’apprentissage d’un modèle, mais utiliser un appel RODBC incorporé pour obtenir d’autres facteurs, effectuer des recherches ou obtenir de nouvelles données de sources externes telles que des fichiers texte ou Excel.

  Le code suivant illustre un appel RODBC incorporé dans un script R :

    ```R
    library(RODBC);
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    dbhandle <- odbcDriverConnect(connStr)
    OutputDataSet <- sqlQuery(dbhandle, "select * from table_name");
    ```

+ **Autres protocoles**

  Les processus qui peuvent avoir besoin de travailler dans des « blocs » ou de transférer des données en retour à un client distant peuvent aussi utiliser le [format de fichier XDF](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf). Le transfert de données proprement dit s’effectue via des objets blob encodés.

## <a name="see-also"></a>Voir aussi

+ [Extension R dans SQL Server](extension-r.md)
+ [Extension Python dans SQL Server](extension-python.md)