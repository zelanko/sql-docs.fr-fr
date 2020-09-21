---
title: Présentation des extensions de langage SQL Server
titleSuffix: ''
description: Les extensions de langage sont une fonctionnalité de SQL Server utilisée pour l’exécution de code externe. Dans SQL Server 2019, Java est pris en charge. Les données relationnelles peuvent être utilisées dans le code externe avec le framework d’extensibilité.
author: dphansen
ms.author: davidph
ms.date: 08/19/2020
ms.topic: overview
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3877e08c3f8976fc6a5c0aedfca594b8dee165a6
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88645924"
---
# <a name="what-is-sql-server-language-extensions"></a>Présentation des extensions de langage SQL Server
[!INCLUDE [SQL Server 2019 and later](../includes/applies-to-version/sqlserver2019.md)]

Les extensions de langage sont une fonctionnalité de SQL Server utilisée pour l’exécution de code externe. Les données relationnelles peuvent être utilisées dans le code externe à l’aide du [framework d’extensibilité](concepts/extensibility-framework.md).

Dans SQL Server 2019, Java est pris en charge. Le runtime Java par défaut est Zulu Open JRE. Vous pouvez également utiliser un autre JRE ou SDK Java.

> [!NOTE]
> Pour exécuter Python ou R dans SQL Server, consultez la documentation [Machine Learning Services](../machine-learning/sql-server-machine-learning-services.md).

## <a name="what-you-can-do-with-language-extensions"></a>Ce que vous pouvez faire avec les extensions de langage

Les extensions de langage utilisent le framework d’extensibilité pour exécuter du code externe. L’exécution du code est isolée des processus du moteur de base, mais entièrement intégrée à l’exécution des requêtes SQL Server. Les extensions de langage vous permettent d’exécuter du code là où résident les données, éliminant ainsi la nécessité de tirer (pull) les données du réseau.

Les langages externes sont définis avec [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql). La procédure stockée système [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) sert d’interface pour l’exécution du code.

Les extensions de langage offrent plusieurs avantages :

+ Sécurité des données. Le fait de rapprocher l’exécution du langage externe de la source de données évite les déplacements de données inutiles ou non sécurisés.
+ Vitesse. Les bases de données sont optimisées pour les opérations basées sur un jeu. Les récentes innovations dans le domaine des bases de données, notamment les tables en mémoire, permettent d’obtenir rapidement des résumés et des agrégations et constituent un complément parfait à la science des données.
+ Facilité de déploiement et d’intégration. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] centralise les opérations pour de nombreuses autres applications et tâches de gestion des données. En utilisant des données qui résident dans la base de données, vous avez la certitude que les données utilisées par Java sont cohérentes et à jour.

## <a name="how-to-get-started"></a>Pour commencer

### <a name="step-1-install-the-software"></a>Étape 1 : Installer le logiciel

+ [Extensions de langage SQL Server sur Windows](install/install-sql-server-language-extensions-on-windows.md)
+ [Extensions de langage SQL Server sur Linux](../linux/sql-server-linux-setup-language-extensions.md)

### <a name="step-2-configure-a-development-tool"></a>Étape 2 : Configurer un outil de développement

Les développeurs écrivent généralement du code sur leur propre ordinateur portable ou station de travail de développement. Avec les extensions de langage dans SQL Server, ce processus reste le même. Une fois l’installation terminée, vous pouvez exécuter du code Java sur SQL Server.

+ **Utilisez l’IDE de votre choix** pour développer du code Java.

+ **Installez le [kit SDK d’extensibilité Microsoft pour Java](how-to/extensibility-sdk-java-sql-server.md)** pour exécuter du code Java sur SQL Server.

+ **Utilisez [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is) ou [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)** pour exécuter du code externe sur SQL Server.

+ **Utilisez la procédure stockée système [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)** pour exécuter votre code Java sur SQL Server.

### <a name="step-3-write-your-first-code"></a>Étape 3 : Écrire du code

Exécutez du code Java à partir d’un script T-SQL :

+ [Tutoriel : Expressions régulières avec Java](tutorials/search-for-string-using-regular-expressions-in-java.md)

## <a name="limitations"></a>Limites

+ Le nombre de valeurs dans les mémoires tampons d’entrée et de sortie ne peut pas dépasser `MAX_INT (2^31-1)`, car il s’agit du nombre maximal d’éléments pouvant être alloués dans un tableau dans Java.

## <a name="next-steps"></a>Étapes suivantes

+ Installer les [extensions de langage SQL Server sur Windows](install/install-sql-server-language-extensions-on-windows.md) ou [sur Linux](../linux/sql-server-linux-setup-language-extensions.md)
+ Installer le [kit SDK d’extensibilité Microsoft pour Java](how-to/extensibility-sdk-java-sql-server.md).
