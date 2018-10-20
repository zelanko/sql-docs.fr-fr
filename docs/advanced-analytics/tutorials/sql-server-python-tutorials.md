---
title: Didacticiels de SQL Server Python | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 5cafb253cea118148bd654ea770234843f742838
ms.sourcegitcommit: b1990ec4491b5a8097c3675334009cb2876673ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49383334"
---
# <a name="sql-server-python-tutorials"></a>Didacticiels de SQL Server Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article fournit une liste des didacticiels et des exemples qui illustrent l’utilisation de Python avec SQL Server 2017. Grâce à ces exemples et des démonstrations, vous allez apprendre :

+ L’exécution de Python à partir de T-SQL
+ Quelles sont les contextes de calcul locaux et distants, et comment vous pouvez exécuter le code Python à l’aide de l’ordinateur SQL Server
+ Comment encapsuler du code Python dans une procédure stockée
+ Optimisation du code Python pour un environnement de production SQL
+ Scénarios réels pour l’incorporation d’apprentissage automatique dans les applications

Pour plus d’informations sur les exigences et le programme d’installation, consultez [conditions préalables](#bkmk_Prerequisites).

## <a name="bkmk_pythontutorials"></a>Didacticiels sur Python

+ [Exécution de Python dans T-SQL](run-python-using-t-sql.md)

   Découvrez les principes fondamentaux de l’appel de Python dans T-SQL, en utilisant le mécanisme d’extensibilité qui veulent dans SQL Server 2016.

+ [Créer un modèle machine learning dans Python à l’aide de revoscalepy](use-python-revoscalepy-to-create-model.md)

   Cette leçon montre comment vous pouvez exécuter le code à partir d’un terminal de Python à distance, à l’aide du contexte de calcul de SQL Server. Vous devez connaître un peu avec les environnements et outils de Python. Exemple de code est fourni qui crée un modèle à l’aide **rxLinMod**, à partir du nouveau **revoscalepy** bibliothèque. 

+ [Analytique en base de données Python pour les développeurs SQL](sqldev-in-database-python-for-sql-developers.md)

    Cette procédure pas à pas de bout en bout montre le processus de génération d’une solution complète de Python à l’aide de procédures stockées T-SQL. Tout le code Python est inclus.


## <a name="python-samples"></a>Exemples Python

Ces exemples et les démonstrations fournies par l’équipe de développement SQL Server mettez en surbrillance les façons dont vous pouvez utiliser analytique incorporée dans les applications réelles.

+ [Créer un modèle prédictif à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

  Découvrez comment une entreprise de location de skis peut utiliser machine learning pour prédire les locations à venir, qui permet du plan d’activités et du personnel pour répondre à la demande future.

  > [!TIP]
  > Inclut désormais la notation native à partir de modèles de Python !

+ [Exécuter le client clustering à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/)

    Découvrez comment utiliser l’algorithme de Kmeans pour effectuer la mise en cluster non supervisé des clients.

## <a name="see-also"></a>Voir aussi

[Didacticiels R pour SQL Server](sql-server-r-tutorials.md)
