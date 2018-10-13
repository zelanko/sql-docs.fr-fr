---
title: Didacticiels de SQL Server Python | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 541675c22ddbe347f67119d8cba82f75955382e6
ms.sourcegitcommit: ce4b39bf88c9a423ff240a7e3ac840a532c6fcae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48877983"
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

## <a name="bkmk_Prerequisites"></a>Conditions préalables

Pour utiliser ces didacticiels, vous devez disposer de SQL Server 2017, et vous devez installer explicitement, puis activez la fonctionnalité, Machine Learning Services (en base de données). 

SQL Server 2017 prend en charge les langages R et Python, mais aucune n’est installé ou activé par défaut. Exécution de Python nécessite que l’infrastructure d’extensibilité soit activée et que vous sélectionnez Python comme la langue à installer. 

### <a name="post-installation-configuration-tips"></a>Conseils de configuration de post-installation

Après avoir exécuté le programme d’installation de SQL Server, vous devrez peut-être effectuer quelques étapes supplémentaires pour vous assurer que Python et SQL Server communiquent :

+ Activer la fonctionnalité de l’exécution de script externe en exécutant `sp_configure 'external scripts enabled', 1`.
+ Redémarrez le serveur. 
+ Ouvrez le **Services** Panneau de configuration pour vérifier si Launchpad a démarré. 
+ Assurez-vous que le service qui appelle le runtime externe dispose des autorisations nécessaires. Pour plus d’informations, consultez [activer l’authentification implicite](../security/add-sqlrusergroup-to-database.md).
+ Ouvrir un port sur le pare-feu pour SQL Server et d’activer les protocoles réseau requis.
+ Assurez-vous que votre compte de connexion SQL ou un compte d’utilisateur Windows dispose des autorisations nécessaires pour se connecter au serveur, pour lire les données et à créer des objets de base de données requis par l’exemple.

Consultez cet article pour certains problèmes courants : [résolution des problèmes des Services Machine Learning](../machine-learning-troubleshooting-faq.md)

### <a name="resource-management"></a>Gestion des ressources

Vous pouvez installer R et Python sur le même ordinateur, mais en cours d’exécution à la fois peut nécessiter des ressources importantes. Si vous obtenez des erreurs « mémoire insuffisante », ou si l’exécution de travaux machine learning est que le principal destiné à l’utilisation du serveur, vous pouvez réduire la quantité de mémoire est allouée au moteur de base de données. Pour plus d’informations, consultez [gestion et surveillance de Python dans SQL Server](../python/managing-and-monitoring-python-solutions.md).

## <a name="see-also"></a>Voir aussi

[Didacticiels R pour SQL Server](sql-server-r-tutorials.md)
