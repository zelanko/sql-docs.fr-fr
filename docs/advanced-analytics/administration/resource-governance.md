---
title: Gouvernance des ressources pour l’exécution du script R et Python - SQL Server Machine Learning
description: Allouer de mémoire RAM, le processeur et e/s pour les charges de travail R et Python sur l’instance du moteur de base de données SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/10/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 72883c8e5bc42ca7f149d17cff530bcf639bdf25
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53431382"
---
# <a name="resource-governance-for-machine-learning-in-sql-server"></a>Gouvernance des ressources pour machine learning dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Science des données et les algorithmes d’apprentissage sont intensifs. Selon les priorités de la charge de travail, vous devrez peut-être augmenter les ressources disponibles pour la science des données ou diminution allocation si l’exécution du script R et Python amoindrit les performances d’autres services qui s’exécutent simultanément. 

Lorsque vous avez besoin rééquilibrer la distribution des ressources système pour plusieurs charges de travail, vous pouvez utiliser [du gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md) pour allouer des UC, e/s physiques et les ressources de mémoire consommées par les runtimes externes pour R et Python. Si vous passez des allocations de ressources, souvenez-vous que vous devrez peut-être également réduire la quantité de mémoire réservée pour d’autres charges de travail et les services. 

> [!NOTE] 
> Gouverneur de ressources est une fonctionnalité Enterprise Edition.

## <a name="default-allocations"></a>Allocations par défaut

Par défaut, les runtimes de script externe pour l’apprentissage sont limités à pas plus de 20 % de mémoire. Cela dépend de votre système, mais en général, vous pouvez trouver cette limite pas adaptée pour les tâches d’apprentissage automatique graves telles que l’apprentissage d’un modèle ou la prévision sur plusieurs lignes de données. 

## <a name="use-resource-governor-to-control-resourcing"></a>Utiliser Resource Governor pour contrôler les ressources
 
Par défaut, les processus externes utilisent jusqu'à 20 % de mémoire totale hôte sur le serveur local. Vous pouvez modifier le pool de ressources par défaut pour apporter des modifications de l’échelle du serveur, avec R et processus Python utilisant toute capacité vous rendre disponible pour les processus externes.

Ou bien, vous pouvez construire personnalisé *pools de ressources externes*, classifieurs, et des groupes de charges de travail associés pour déterminer l’allocation de ressources pour les demandes provenant des programmes spécifiques, d’hôtes ou d’autres critères qui vous fournissez. Un pool de ressources externe est un type de pool de ressources introduit dans [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] pour aider à gérer les processus R et Python externes au moteur de base de données.

1. [Activer la gouvernance des ressources](https://docs.microsoft.com/sql/relational-databases/resource-governor/enable-resource-governor) (elle est désactivée par défaut).

2. Exécutez [CREATE EXTERNAL RESOURCE POOL](https://docs.microsoft.com/sql/t-sql/statements/create-external-resource-pool-transact-sql) pour créer et configurer le pool de ressources, suivi de [ALTER RESOURCE GOVERNOR](https://docs.microsoft.com/sql/t-sql/statements/alter-resource-governor-transact-sql) mettre en œuvre.

3. Créez un groupe de charge de travail pour les allocations granulaires, par exemple entre l’apprentissage et l’évaluation.

4. Créer un classifieur pour intercepter des appels pour le traitement externe.

5. Exécuter des requêtes et les procédures qui utilisent les objets que vous avez créé.

Pour une procédure pas à pas, consultez [comment créer un pool de ressources pour les scripts R et Python externes](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md) pour obtenir des instructions pas à pas.

Pour une introduction à la terminologie et les concepts généraux, consultez [Pool de ressources du gouverneur de ressources](../../relational-databases/resource-governor/resource-governor-resource-pool.md).

## <a name="processes-under-resource-governance"></a>Processus de gouvernance des ressources
  
 Vous pouvez utiliser un *pool de ressources externes* pour gérer les ressources utilisées par les exécutables suivants sur une instance du moteur de base de données :

+ Rterm.exe lorsque appelée localement à partir de SQL Server ou appelée à distance avec SQL Server comme contexte de calcul à distance
+ Python.exe lorsque appelée localement à partir de SQL Server ou appelée à distance avec SQL Server comme contexte de calcul à distance
+ BxlServer.exe et les processus satellites
+ Processus satellites lancés par Launchpad, tels que PythonLauncher.dll
  
> [!NOTE]
> Gestion directe du service Launchpad à l’aide du gouverneur de ressources n’est pas pris en charge. LaunchPad est un service approuvé qui peut uniquement les lanceurs d’hôte fournis par Microsoft. Les lanceurs approuvés sont explicitement configurés pour éviter de consommer trop de ressources.
  
## <a name="see-also"></a>Voir aussi

+ [Gérer l’intégration de machine learning](../r/managing-and-monitoring-r-solutions.md)
+ [Créer un pool de ressources pour Machine Learning](../r/how-to-create-a-resource-pool-for-r.md)
+ [Pools de ressources du gouverneur de ressources](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
