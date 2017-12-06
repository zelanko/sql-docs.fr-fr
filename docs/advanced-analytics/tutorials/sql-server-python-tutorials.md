---
title: Didacticiels de SQL Server Python | Documents Microsoft
ms.custom: SQL2016_New_Updated
ms.date: 09/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2017
dev_langs: Python
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: 2ad3195e695d7e99a812b5eb6c3987f9553e248c
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
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

+ [Analytique Python de la base de données pour les développeurs SQL](sqldev-in-database-python-for-sql-developers.md)

  NOUVEAU ! Générez une solution complète de Python à l’aide de procédures stockées T-SQL. Tout le code Python est inclus.

+ [Déployer et utiliser un modèle de Python](..\python\publish-consume-python-code.md)

  Découvrez comment déployer un modèle de Python à l’aide de la dernière version du serveur de Microsoft Machine Learning.

## <a name="python-samples"></a>Exemples de Python

Ces exemples et les démonstrations fournies par l’équipe de développement SQL Server mettez en surbrillance les façons dont vous pouvez utiliser analytique incorporées dans les applications réelles.

+ [Créer un modèle prédictif à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

  Découvrez comment une entreprise de location ski peut utiliser d’apprentissage prévoir les futures Locations, ce qui vous permet du plan d’entreprise et le personnel pour répondre à la demande.

  > [!TIP]
  > Inclut désormais un score natif à partir de modèles de Python !

+ [Exécuter le client clusters à l’aide de Python et SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/)

    Découvrez comment utiliser l’algorithme de Kmeans pour effectuer de clustering non supervisé de clients.

## <a name="bkmk_Prerequisites"></a>Conditions préalables

Pour utiliser ces didacticiels, vous devez avoir installé SQL Server 2017 Machine Learning Services (de-de base de données). SQL Server 2017 prend en charge R ou Python. Toutefois, vous devez installer l’infrastructure d’extensibilité qui prend en charge d’apprentissage et sélectionnez la langue à installer Python. Sur le même ordinateur, vous pouvez installer R et Python.

> [!NOTE]
>
> Prise en charge de Python est une nouvelle fonctionnalité dans SQL Server 2017 et requiert la version CTP 2.0 ou version ultérieure. Bien que la fonctionnalité est en version préliminaire et non pris en charge pour les environnements de production, nous vous invitons à essayer et envoyer vos commentaires.

**SQL Server 2017**

Après avoir exécuté le programme d’installation de SQL Server, n’oubliez pas ces étapes importantes :

+ Activez la fonctionnalité d’exécution de script externe en exécutant `sp_configure 'external scripts enabled', 1`.
+ Redémarrez le serveur.
+ Assurez-vous que le service qui appelle le runtime externe dispose des autorisations nécessaires.
+ Assurez-vous que votre compte de connexion SQL ou un compte d’utilisateur Windows dispose des autorisations nécessaires pour se connecter au serveur, pour lire des données et à créer des objets de base de données requis par l’exemple.

Si vous rencontrez des problèmes, consultez cet article pour certains problèmes courants : [dépannage Machine Learning Services](../machine-learning-troubleshooting-faq.md)

## <a name="see-also"></a>Voir aussi

[Didacticiels R pour SQL Server](sql-server-r-tutorials.md)
