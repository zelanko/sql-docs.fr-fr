---
title: Didacticiels de SQL Server Python | Documents Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 08/29/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
caps.latest.revision: 1
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b891cda72d5a69aafe461918674218fd3279c423
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="sql-server-python-tutorials"></a>Didacticiels de SQL Server Python

Cet article fournit une liste des didacticiels et des exemples qui illustrent l’utilisation de Python avec SQL Server 2017. Grâce à ces exemples et les démonstrations, vous allez apprendre :

+ L’exécution de Python à partir de T-SQL
+ Quelles sont les contextes de calcul locaux et distants, et comment vous pouvez exécuter le code Python à l’aide de l’ordinateur SQL Server
+ Comment faire pour encapsuler le code Python dans une procédure stockée
+ Optimisation du code Python pour un environnement de production SQL
+ Des scénarios concrets pour l’incorporation d’apprentissage dans les applications

Pour plus d’informations sur le programme d’installation, consultez [conditions préalables](#bkmk_Prerequisites).

## <a name="bkmk_pythontutorials"></a>Didacticiels de Python

+ [En cours d’exécution de Python dans T-SQL](run-python-using-t-sql.md)

   Découvrez les principes fondamentaux de l’appel de Python dans T-SQL, en utilisant le mécanisme d’extensibilité fait son apparition dans SQL Server 2016.

+ [Créer un modèle dans Python à l’aide de revoscalepy d’apprentissage](use-python-revoscalepy-to-create-model.md)

   Vous allez créer un modèle à l’aide de **rxLinMod**, à partir du nouveau **revoscalepy** bibliothèque. Vous allez lancer le code à partir d’un terminal de Python à distance, mais la modélisation aura lieu dans le contexte de calcul de SQL Server.

+ [Créer un modèle prédictif avec Python (GitHub)](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/machine-learning-services/python/getting-started/rental-prediction)

  Créer un modèle d’apprentissage automatique pour prédire la demande pour une entreprise de location ski et tiens ce modèle pour la prédiction à la demande quotidienne à l’aide de procédures stockées. Toutes les données et code est fourni.

+ [Analytique Python de la base de données pour les développeurs SQL](sqldev-in-database-python-for-sql-developers.md)

  NOUVEAU ! Générez une solution complète de Python à l’aide de procédures stockées T-SQL. Tout le code Python est inclus.

+ [Déployer et utiliser un modèle de Python](..\python\publish-consume-python-code.md)

  Découvrez comment déployer un modèle de Python à l’aide de la dernière version du serveur de Microsoft Machine Learning.

## <a name="python-samples"></a>Exemples de Python

Ces exemples et les démonstrations fournies par l’équipe de développement SQL Server mettez en surbrillance les façons dont vous pouvez utiliser analytique incorporées dans les applications réelles.

+ [Créer un modèle prédictif à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

  Découvrez comment une entreprise de location ski peut utiliser d’apprentissage prévoir les futures Locations, ce qui vous permet du plan d’entreprise et le personnel pour répondre à la demande.

+ [NOUVEAU ! Exécuter le client clusters à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/)

    Découvrez comment utiliser l’algorithme de Kmeans pour effectuer de clustering non supervisé de clients.

## <a name="bkmk_Prerequisites"></a>Conditions préalables

Pour utiliser ces didacticiels, vous devez avoir installé SQL Server 2017 Machine Learning Services (de-de base de données). SQL Server 2017 prend en charge R ou Python. Toutefois, vous devez installer l’infrastructure d’extensibilité qui prend en charge d’apprentissage et sélectionnez la langue à installer Python. Sur le même ordinateur, vous pouvez installer R et Python.

> [!NOTE]
>
> Prise en charge de Python est une nouvelle fonctionnalité dans SQL Server 2017 et requiert la version CTP 2.0 ou version ultérieure. Bien que la fonctionnalité est en version préliminaire et non pris en charge pour les environnements de production, nous vous invitons à essayer et envoyer vos commentaires.

**SQL Server 2017**

Après avoir exécuté le programme d’installation de SQL Server, n’oubliez pas ces étapes importantes :

+ Activez la fonctionnalité d’exécution de script externe en exécutant`sp_configure 'external scripts enabled', 1`
+ Redémarrer le serveur
+ Assurez-vous que le service qui appelle le runtime externe dispose des autorisations nécessaires
+ Assurez-vous que votre compte de connexion SQL ou un compte d’utilisateur Windows dispose des autorisations nécessaires pour se connecter au serveur, pour lire des données et à créer des objets de base de données requis par l’exemple

Si vous rencontrez des problèmes, consultez cet article pour certains problèmes courants : [dépannage Machine Learning Services](../machine-learning-troubleshooting-faq.md)

## <a name="see-also"></a>Voir aussi

[Didacticiels de R pour SQL Server](sql-server-r-tutorials.md)

