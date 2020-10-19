---
title: Présentation des extensions de langage SQL Server
titleSuffix: ''
description: Les extensions de langage sont une fonctionnalité de SQL Server utilisée pour l’exécution de code externe. Dans SQL Server 2019, Java, Python et R sont pris en charge. Les données relationnelles peuvent être utilisées dans le code externe avec le framework d’extensibilité.
author: dphansen
ms.author: davidph
ms.date: 10/07/2020
ms.topic: overview
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 09d5643b3a39493843adc0ad2da716b7fda1b332
ms.sourcegitcommit: fe59f8dc27fd633f5dfce54519d6f5dcea577f56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91934904"
---
# <a name="what-is-sql-server-language-extensions"></a>Présentation des extensions de langage SQL Server
[!INCLUDE [SQL Server 2019 and later](../includes/applies-to-version/sqlserver2019.md)]

Les extensions de langage sont une fonctionnalité de SQL Server utilisée pour l’exécution de code externe. Les données relationnelles peuvent être utilisées dans le code externe à l’aide du [framework d’extensibilité](concepts/extensibility-framework.md).

Dans SQL Server 2019, Java, Python et R sont pris en charge.

> [!NOTE]
> Pour exécuter Python ou R dans SQL Server, consultez la documentation [SQL Machine Learning](../machine-learning/index.yml). Avec SQL Server 2019 et versions ultérieures, vous pouvez utiliser un runtime Python et R personnalisé avec les extensions de langage. Pour plus d’informations, consultez le [runtime personnalisé Python](../machine-learning/install/custom-runtime-python.md) et le [runtime personnalisé R](../machine-learning/install/custom-runtime-r.md).

## <a name="what-you-can-do-with-language-extensions"></a>Ce que vous pouvez faire avec les extensions de langage

Les extensions de langage utilisent le framework d’extensibilité pour exécuter du code externe. L’exécution du code est isolée des processus du moteur de base, mais entièrement intégrée à l’exécution des requêtes SQL Server. Vous pouvez exécuter du code à la source des données, ce qui évite d’avoir à extraire des données sur le réseau.

Les langages externes sont définis avec [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md). La procédure stockée système [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) sert d’interface pour l’exécution du code.

Les extensions de langage offrent plusieurs avantages :

+ Sécurité des données. Le fait de rapprocher l’exécution du langage externe de la source de données évite les déplacements de données inutiles ou non sécurisés.
+ Vitesse. Les bases de données sont optimisées pour les opérations basées sur un jeu. Les récentes innovations dans le domaine des bases de données, notamment les tables en mémoire, permettent d’obtenir rapidement des résumés et des agrégations et constituent un complément parfait à la science des données.
+ Facilité de déploiement et d’intégration. [!INCLUDE [ssNoVersion](../includes/ssnoversion-md.md)] centralise les opérations pour de nombreuses autres applications et tâches de gestion des données. En utilisant des données dans la base de données, vous avez la certitude que les données utilisées par l’extension de langage sont cohérentes et à jour.

## <a name="next-steps"></a>Étapes suivantes

+ Installer le [runtime personnalisé Python pour SQL Server](../machine-learning/install/custom-runtime-python.md)
+ Installer le [runtime personnalisé R pour SQL Server](../machine-learning/install/custom-runtime-r.md)
+ Installer les [extensions de langage SQL Server sur Windows](install/install-sql-server-language-extensions-on-windows.md) ou [sur Linux](../linux/sql-server-linux-setup-language-extensions.md)
+ Installer le [kit SDK d’extensibilité Microsoft pour Java](how-to/extensibility-sdk-java-sql-server.md).
