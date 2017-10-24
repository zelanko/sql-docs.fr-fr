---
title: "Différences de fonctionnalités de machine learning entre les éditions de SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 08/22/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b33a3e2-04d3-4bad-9335-9568ae09db0b
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b9b520b7fc7e97498f4b46a43ad991558025123a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---

# <a name="differences-in-machine-learning-features-between-editions-of-sql-server"></a>Différences de fonctionnalités de machine learning entre les éditions de SQL Server
 
 Prise en charge pour l’apprentissage est disponible dans les éditions suivantes de SQL Server 2016 et SQL Server 2017 :

## <a name="summary-of-differences"></a>Résumé des différences

-   **Enterprise Edition**
    
     SQL Server 2017 inclut Machine Learning Services (dans bases de données. SQL Server 2016 comprend les Services de R. Cette fonctionnalité prend en charge dans base de données analytique dans SQL Server, y compris l’utilisation de SQL Server en tant qu’un contexte de calcul.
     
     SQL Server 2017 inclut Microsoft Machine Learning Server (autonome). SQL Server 2016 inclut Microsoft R Server (autonome). Cette fonctionnalité prend en charge à l’Opérationnalisation d’apprentissage automatique qui ne nécessite pas l’utilisation de SQL Server en tant qu’un contexte de calcul.

     Il n’existe aucune restriction sur ces fonctionnalités dans Enterprise Edition, ce qui permet d’optimiser les performances et l’évolutivité et la parallélisation de diffusion en continu. Cette édition optimise également l’utilisation de plateformes pris en charge pour la diffusion en continu et en parallèle.
     
     Analytique dans base de données à l’aide de SQL Server prend en charge la gouvernance des ressources de scripts externes pour personnaliser l’utilisation des ressources serveur.
     
     Les éditions plus récentes de Microsoft R Server incluent une version améliorée du moteur à l’Opérationnalisation qui prend en charge le déploiement rapid, sécurisé et le partage des solutions R. Pour plus d’informations, consultez [mrsdeploy](https://docs.microsoft.com/r-server/r-reference/mrsdeploy/mrsdeploy-package).

-   **Developer Edition**

     Fonctionnalités identiques à celles d’Enterprise Edition ; toutefois, Developer Edition ne peut pas être utilisée dans les environnements de production.  
  
-   **Standard Edition**

     Toutes les fonctionnalités de la base de données analytique a inclus avec l’édition entreprise, à l’exception de gouvernance des ressources. Performances et l’échelle est également limité : les données qui peuvent être traitées doivent tenir dans la mémoire du serveur et le traitement est limité à un thread de calcul unique, même si vous utilisez la **RevoScaleR** fonctions.
  
-   **Express et Web des éditions**
  
     Uniquement Express Edition with Advanced Services inclut les fonctionnalités d’apprentissage automatique. Les limitations des performances sont similaires à celles de l’édition Standard Edition. Édition Web n’est pas prévue pour des tâches telles que la création de modèles d’apprentissage automatique ; Toutefois, vous pouvez utiliser la fonction de prédiction pour effectuer le calcul de score à l’aide de modèles formés ailleurs.

-   **Azure SQL Database**
  
     Fonctionnalités de la machine learning tels que R et Python de script ne sont pas actuellement pris en charge dans la base de données SQL Azure.
     
     Pour plus d’informations et des annonces relatives lorsque cette fonctionnalité sera disponible, consultez le blog de SQL Server : [Python dans SQL Server 2017 : amélioré dans base de données d’apprentissage](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)


### <a name="languages-supported-in-all-editions"></a>Langues prises en charge dans toutes les éditions

Les langues d’apprentissage machine suivantes sont prises en charge pour toutes les éditions :

+ SQL Server 2017 : R et Python
+ SQL Server 2016 : R uniquement

Microsoft R Open est fourni avec toutes les éditions.

Microsoft R Client peut fonctionner avec toutes les éditions.

## <a name="machine-learning-in-enterprise-edition"></a>Apprentissage automatique dans Enterprise Edition

Performances des solutions de machine learning [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est censé dépassent généralement des implémentations à l’aide de R classique, étant donné le même matériel. Car, dans SQL Server, des solutions R peuvent être exécutées à l’aide des ressources du serveur et parfois distribuées à plusieurs processus à l’aide de la **RevoScaleR** fonctions. 

Performances n’a pas été évalué pour les solutions de Python, comme la fonction est toujours en cours de développement, mais certains avantages de la mêmes application sont attendus.

Les utilisateurs pourront également voir des différences considérables des performances et une extensibilité accrues pour la même solution d’apprentissage s’exécuter dans Visual Studio d’Enterprise Edition. Standard Edition. Raisons prennent en charge parallèle traitement, l’augmentation de threads disponibles pour l’apprentissage et de diffusion en continu (ou de segmentation), ce qui permet les fonctions RevoScaleR gérer plus de données que vous pouvez tenir dans la mémoire. 

Toutefois, les performances même sur du matériel identiques peuvent être affectées par de nombreux facteurs en dehors du code R ou Python. Ces facteurs incluent les demandes concurrentes sur les ressources de serveur, le type de plan de requête qui est créé, les modifications de schéma, la nécessité de mettre à jour les statistiques ou en créer un nouveau plan de requête, la fragmentation et bien plus encore. Il est possible qu’une procédure stockée contenant du code R ou Python peut s’exécuter dans les secondes sous une charge de travail, mais prennent en minutes lorsque d’autres services en cours d’exécution.  Par conséquent, nous vous recommandons de surveiller plusieurs aspects des performances du serveur, y compris la mise en réseau pour les contextes de calcul à distance, lors de la mesure des performances d’une machine learning.

Nous recommandons également de configurer [du gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md) (disponible dans l’édition Enterprise) pour personnaliser la manière que les travaux de script externe sont classés par priorité ou gérées sous des charges de travail lourd du serveur. Vous pouvez définir des fonctions classifieur pour spécifier la source de la tâche de script externe et de hiérarchiser certaines charges de travail, de limiter la quantité de mémoire utilisée par les requêtes SQL et contrôler le nombre de traitements parallèles utilisées dans une charge de travail.

## <a name="machine-learning-in-developer-edition"></a>Apprentissage automatique dans Developer Edition

Developer Edition fournit des performances équivalentes à celles d’Enterprise Edition. Toutefois, l’utilisation de Developer Edition n’est pas prise en charge dans les environnements de production.

## <a name="machine-learning-in-standard-edition"></a>Apprentissage automatique dans l’Édition Standard

Pour la même configuration matérielle, Standard Edition doit offrir des gains de performance par rapport à des packages R standard.

Édition standard ne prend pas en charge le gouverneur de ressources. À l’aide de la gouvernance des ressources est la meilleure façon de personnaliser les ressources du serveur pour prendre en charge diverses charges de travail telles que le mode d’apprentissage et de calcul de score.

Standard Edition fournit également des performances et une scalabilité limitées par rapport aux éditions Enterprise et Developer. Tous les **RevoScaleR** fonctions et des packages sont inclus avec l’Édition Standard, mais le service qui lance et gère des scripts R est limité dans le nombre de processus, il peut utiliser. En outre, les données traitées par le script doivent tenir dans la mémoire.  Les mêmes restrictions s’appliquent à des solutions qui utilisent **revoscalepy**.

## <a name="machine-learning-in-express-edition-with-advanced-services"></a>Apprentissage automatique dans Express Edition with Advanced Services

Express Edition est soumis aux mêmes limitations que Standard Edition.

## <a name="machine-learning-in-web-edition"></a>Apprentissage de Web Edition

Édition Web ne prend pas en charge l’exécution de scripts R ou Python. Toutefois, vous pouvez utiliser la fonction de prédiction pour effectuer [score native](../sql-native-scoring.md) sur un modèle qui a été formé sur une autre instance de SQL Server ou serveur R et puis enregistré au format binaire.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d'informations, consultez :

+ [Éditions et composants de SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md)
+ [Éditions et composants de SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md)

Pour plus d’informations sur les autres fonctionnalités de SQL Server, consultez :

+ [Fonctionnalités prises en charge par les éditions de SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md) 

Pour plus d’informations sur les fonctionnalités de Microsoft R et comment vous pouvez optimiser votre solution de grands jeux de données, consultez la [Microsoft R Server](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips) documentation.

