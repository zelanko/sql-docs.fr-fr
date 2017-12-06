---
title: "Différences de fonctionnalités de machine learning entre les éditions de SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 11/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b33a3e2-04d3-4bad-9335-9568ae09db0b
caps.latest.revision: "12"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: e599ab78d2b6a6ede13b1da1e6edf5167405fc2c
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="differences-in-machine-learning-features-between-editions-of-sql-server"></a>Différences de fonctionnalités de machine learning entre les éditions de SQL Server
 
 Prise en charge pour l’apprentissage est disponible dans SQL Server 2016 et SQL Server 2017. Cet article répertorie les éditions qui prennent en charge la fonctionnalité, décrit les limitations supplémentaires qui s’appliquent dans les éditions spécifiques et répertorie les fonctionnalités disponibles uniquement dans certaines éditions.

 > [!NOTE]
 > En règle générale, l’apprentissage de SQL Server n’inclut pas le [à l’Opérationnalisation](https://docs.microsoft.com/machine-learning-server/what-is-operationalization) fonctionnalités qui sont incluses dans Microsoft R Server ou serveur de Machine Learning.
 > 
 > Si vous avez besoin de ces fonctionnalités, vous pouvez installer Microsoft R Server ou serveur de Machine Learning séparément, pour prendre en charge le déploiement de modèles prédictifs comme un service web. 

## <a name="summary-of-differences"></a>Résumé des différences

-   **Enterprise Edition**
    
     SQL Server 2017 inclut Machine Learning Services (dans bases de données. SQL Server 2016 comprend les Services de R. Cette fonctionnalité prend en charge dans base de données analytique dans SQL Server, y compris l’utilisation de SQL Server en tant qu’un contexte de calcul.
     
     SQL Server 2017 inclut Microsoft Machine Learning Server (autonome). SQL Server 2016 inclut Microsoft R Server (autonome). Cette fonctionnalité prend en charge à l’Opérationnalisation d’apprentissage automatique qui ne nécessite pas l’utilisation de SQL Server en tant qu’un contexte de calcul.

     Il n’existe aucune restriction sur ces fonctionnalités dans Enterprise Edition, ce qui permet d’optimiser les performances et l’évolutivité et la parallélisation de diffusion en continu. Cette édition optimise également l’utilisation de plateformes pris en charge pour la diffusion en continu et en parallèle. Cela signifie que, contrairement à une édition Standard, les données d’entrée n’a pas besoin d’être chargé en mémoire, mais peut être transmis en continu.
     
     Analytique dans base de données à l’aide de SQL Server prend en charge la gouvernance des ressources de scripts externes pour personnaliser l’utilisation des ressources serveur.
     
     Les éditions plus récentes de Microsoft R Server et de Machine Learning Server incluent une version améliorée du moteur à l’Opérationnalisation qui prend en charge le déploiement rapid, sécurisé et le partage des solutions R. Pour plus d’informations, consultez [tiens analytique avec Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-operationalization).

-   **Developer Edition**

     Fonctionnalités identiques à celles d’Enterprise Edition ; toutefois, Developer Edition ne peut pas être utilisée dans les environnements de production.  
  
-   **Standard Edition**

     Toutes les fonctionnalités de la base de données analytique a inclus avec l’édition entreprise, à l’exception de gouvernance des ressources. Performances et évolutivité sont limitées : les données qui peuvent être traitées doivent tenir dans la mémoire du serveur et le traitement est limité à un thread de calcul unique, même si vous utilisez la **RevoScaleR** fonctions.
  
-   **Express et Web des éditions**
  
     Uniquement Express Edition with Advanced Services inclut les fonctionnalités d’apprentissage automatique. Les limitations des performances sont similaires à celles de l’édition Standard Edition. 
     
     Web Edition n’est pas destinée à être des tâches telles que la création de modèles d’apprentissage automatique. Toutefois, vous pouvez utiliser la fonction de prédiction pour effectuer le calcul de score à l’aide de modèles formés ailleurs.

-   **Azure SQL Database**
  
     Après une version test initial, les Services de R est actuellement **pas** disponibles dans la base de données SQL Azure, en attente d’un développement ultérieur. 

### <a name="external-script-languages-supported"></a>Prise en charge les langages de script externe

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

Édition développeur fournit des performances équivalentes à celles de l’édition Enterprise.

Utilisation de Developer Edition n’est pas prise en charge pour les environnements de production.

## <a name="machine-learning-in-standard-edition"></a>Apprentissage automatique dans l’Édition Standard

Pour la même configuration matérielle, Standard Edition doit offrir des gains de performance par rapport à des packages R standard.

Édition standard ne prend pas en charge le gouverneur de ressources. Édition standard fournit également des performances limitées et évolutivité par rapport aux éditions Enterprise et Developer.

Tous les **RevoScaleR** fonctions et des packages sont inclus avec l’Édition Standard, mais le service qui lance et gère des scripts R est limité dans le nombre de processus, il peut utiliser. En outre, les données traitées par le script doivent tenir dans la mémoire.

Les mêmes restrictions s’appliquent à des solutions qui utilisent **revoscalepy**.

## <a name="machine-learning-in-express-edition-with-advanced-services"></a>Apprentissage automatique dans Express Edition with Advanced Services

Express Edition est soumis aux mêmes limitations que Standard Edition.

## <a name="machine-learning-in-web-edition"></a>Apprentissage de Web Edition

Édition Web ne prend pas en charge l’exécution de scripts R ou Python. Toutefois, vous pouvez utiliser la [PREDICT](../../t-sql/queries/predict-transact-sql.md) fonction à exécuter [score native](../sql-native-scoring.md) sur un modèle qui a été formé sur une autre instance de SQL Server ou serveur R et puis enregistré au format binaire.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d'informations, consultez :

+ [Éditions et composants de SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md)
+ [Éditions et composants de SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md)

Pour plus d’informations sur les autres fonctionnalités de SQL Server, consultez :

+ [Éditions et fonctionnalités prises en charge de SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md) 

Pour plus d’informations sur la façon dont vous pouvez optimiser votre solution de grands jeux de données, consultez [obtenir des conseils sur le calcul des données volumineuses dans R](https://docs.microsoft.com/machine-learning-server/r/tutorial-large-data-tips) documentation.
