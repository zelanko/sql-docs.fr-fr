---
title: Propriétés du cache de la | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Income property
- InitialBonus property
- PercentScanPerPrice property
- FileStore properties
- BackgroundTrimCost property
- Tax property
- PerformanceTrace property
- MinimumBalance property
- UnbufferedThreshold property
- BackgroundTrimAmount property
- MaximumBalance property
- MemoryLimitMin property
- MemoryLimit property
ms.assetid: 580cf0aa-7425-4d48-aa8d-128f5b488fcd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fe11b7a9cda6b3e75cb97faa17a381e2b0ea1afe
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66069087"
---
# <a name="filestore-properties"></a>FileStore, propriété
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les propriétés du serveur de cache de fichiers répertoriées dans les tableaux suivants. Toutes ces propriétés sont des propriétés avancées que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Pour plus d'informations sur les autres propriétés de serveur et la façon de les configurer, consultez [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **S'applique à :** mode serveur multidimensionnel et tabulaire  
  
## <a name="properties"></a>Propriétés  
 `MemoryLimit`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MemoryLimitMin`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `PercentScanPerPrice`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `PerformanceTrace`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `RandomFileAccessMode`  
 Propriété booléenne qui indique si les fichiers de base de données et les fichiers mis en cache sont accessibles en mode d'accès aléatoire aux fichiers. Cette propriété est désactivée par défaut. Par défaut, Analysis Services ne définit pas la balise d'accès aléatoire aux fichiers lors de l'ouverture des fichiers de données de partition pour l'accès en lecture.  
  
 Sur les systèmes haut de gamme, en particulier ceux qui comportent d'importantes ressources de mémoire et plusieurs nœuds NUMA, il peut être avantageux d'utiliser l'accès aléatoire aux fichiers. En mode d'accès aléatoire, Windows ignore les opérations de mappage de page qui lisent des données à partir du disque dans le cache des fichiers système, réduisant ainsi le conflit dans le cache.  
  
 Vous devrez effectuer des tests de comparaison afin de déterminer si les performances de requête sont améliorées lorsque vous modifiez cette propriété. Pour connaître les meilleures pratiques concernant l'exécution de tests de comparaison, y compris l'effacement du cache et les erreurs courantes à éviter, consultez le document [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539). Pour plus d’informations sur les compromis de l’utilisation de cette propriété [https://support.microsoft.com/kb/2549369](https://support.microsoft.com/kb/2549369), consultez.  
  
 Pour afficher ou modifier cette propriété dans Management Studio, activez la liste des propriétés avancées dans la page des propriétés du serveur. Vous pouvez également modifier la propriété dans le fichier msmdsrv.ini. Le redémarrage du serveur est recommandé après la définition de cette propriété ; sinon, les fichiers déjà ouverts vont continuer à être accessibles selon le mode précédent.  
  
 `UnbufferedThreshold`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="memory-model-category"></a>Catégorie de modèle de mémoire  
 `MemoryModel\Tax`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MemoryModel\Income`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MemoryModel\MaximumBalance`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MemoryModel\MinimumBalance`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MemoryModel\InitialBonus`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les propriétés du serveur dans Analysis Services](server-properties-in-analysis-services.md)   
 [Déterminer le mode serveur d'une instance Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
