---
title: Référence API pour les Services de SQL Server Machine Learning | Documents Microsoft
ms.custom: ''
ms.date: 10/31/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: 77f0e3af1281cd4f6249defff820ccb7b7f5f238
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2018
---
# <a name="api-reference-for-sql-server-machine-learning-services"></a>Référence API pour les Services de SQL Server Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article fournit des liens vers la documentation de référence pour l’apprentissage d’API utilisées par SQL Server.

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 d’apprentissage automatique Services

Dans la plupart des cas, SQL Server utilise les mêmes bibliothèques R et Python fournis dans Microsoft R Server et Microsoft Machine Learning Server. 

> [!NOTE]
> Documentation pour toutes les API est dérivée de code source et n’a pas été modifiée. Si vous constatez des erreurs, ajoutez un commentaire dans la documentation de référence des API. 

## <a name="r"></a>R

+ [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)

    Algorithmes évolutives qui prennent en charge de plusieurs sources de données et les contextes de calcul à distance.

+ [MicrosoftML](https://docs.microsoft.com/machine-learning-serverr-reference/microsoftml/microsoftml-package)

    Rapide et évolutif, apprentissage algorithmes et les transformations de RevoScaleR nécessite de r.

+ [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr)

   Lit le schéma de sources de données OLAP et exécute des requêtes MDX.

+ [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)

    Fonctions d’assistance pour la génération d’une procédure stockée bien formée à partir du code R.

+ [mrsdeploy](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)

   Fonctions permettant d’établir une session à distance dans une application console et pour la publication et la gestion d’un service web qui utilise le code R ou Python.

## <a name="python"></a>Python

+ [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package)

    Équivalent de Python du package RevoScaleR pour le langage R. Prend en charge les mêmes sources de données et les contextes de calcul.

+ [Microsoftml pour Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)

    Équivalent de Python de la MicrosoftML du package pour prend en charge R. les mêmes contextes de calcul et les sources de données et inclut rapides et évolutives et les algorithmes transformations à partir de Microsoft. 

## <a name="related-apis"></a>API associées

+ [Référence des fonctions RevoPEMAR](https://docs.microsoft.com/machine-learning-server/r-reference/revopemar/pemar)

    Prend en charge le développement des algorithmes parallèles

+ [RevoUtils](https://docs.microsoft.com/machine-learning-server/r-reference/revoutils/revoutils)

    Fonctions utilitaires pour une utilisation avec les environnements de RevoScaleR

## <a name="other"></a>Autres

Rubriques « Comment » et des résumés spécifiques à l’utilisation de ces API Python dans SQL Server ou de R sont disponibles ici :

+ [Fonctions scaleR pour travailler avec SQL Server](scaler-functions-for-working-with-sql-server-data.md)
+ [Générer une procédure stockée à l’aide de sqlrutils](generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
+ [Lire les données dans R olapR à l’aide de MDX](how-to-create-mdx-queries-using-olapr.md)
