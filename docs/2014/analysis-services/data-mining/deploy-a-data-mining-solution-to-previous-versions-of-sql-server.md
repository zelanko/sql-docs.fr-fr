---
title: Déployer une solution d’exploration de données dans des versions antérieures de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [Analysis Services]
- holdout [data mining]
- deploy [Analysis Services]
- time series [Analysis Services]
- deploying [Analysis Services - data mining]
- synchronization [Analysis Services]
- deployment [Analysis Services]
ms.assetid: 2715c245-f206-43af-8bf5-e6bd2585477a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dc721d58c69b0275c9846863f761d60db66e5aaf
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66084676"
---
# <a name="deploy-a-data-mining-solution-to-previous-versions-of-sql-server"></a>Déployer une solution d'exploration de données sur des versions antérieures de SQL Server
  Cette section décrit des problèmes de compatibilité connus qui peuvent survenir lorsque vous essayez de déployer un modèle d'exploration de données ou une structure d'exploration de données créée dans une instance de [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] sur une base de données qui utilise SQL Server 2005 Analysis Services, ou lorsque vous déployez des modèles créés dans SQL Server 2005 sur une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Le déploiement sur une instance de SQL Server 2000 Analysis Services n'est pas pris en charge.  
  
 [Déploiement de modèles de séries chronologiques](#bkmk_TimeSeries)  
  
 [Déploiement de modèles avec données d'exclusion](#bkmk_Holdout)  
  
 [Déploiement de modèles avec filtres](#bkmk_Filter)  
  
 [Restauration à partir de sauvegardes de base de données](#bkmk_Backup)  
  
 [Utilisation de la synchronisation de base de données](#bkmk_Synch)  
  
##  <a name="deploying-times-series-models"></a><a name="bkmk_TimeSeries"></a>Déploiement des modèles de série Times  
 L'algorithme MTS (Microsoft Time Series) a été amélioré dans SQL Server 2008 grâce à l'ajout d'un second algorithme complémentaire, ARIMA. Pour plus d’informations sur les modifications apportées à l’algorithme MTS, consultez [Algorithme MTS (Microsoft Time Series)](microsoft-time-series-algorithm.md).  
  
 Par conséquent, les modèles d'exploration de données de série chronologique qui utilisent le nouvel algorithme ARIMA peuvent se comporter différemment lorsqu'ils sont déployés sur une instance de SQL Server 2005 Analysis Services.  
  
 Si vous avez défini explicitement le paramètre PREDICTION_SMOOTHING pour contrôler l'association des modèles ARTXP et ARIMA dans la prédiction, lorsque vous déployez ce modèle sur une instance de SQL Server 2005, Analysis Services déclenche une erreur indiquant que le paramètre n'est pas valide. Pour empêcher cette erreur, vous devez supprimer le paramètre PREDICTION_SMOOTHING et convertir les modèles dans un modèle purement ARTXP.  
  
 Inversement, si vous déployez un modèle de série chronologique créé à l'aide de SQL Server 2005 Analysis Services sur une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], lorsque vous ouvrez le modèle d'exploration de données dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], les fichiers de définition sont convertis d'abord au nouveau format, et deux nouveaux paramètres sont ajoutés par défaut à tous les modèles de série chronologique. Le paramètre FORECAST_METHOD est ajouté avec la valeur par défaut de MIXED, et le paramètre PREDICTION_SMOOTHING est ajouté avec la valeur par défaut de 0.5. Toutefois, le modèle continue à utiliser uniquement ARTXP pour la prévision jusqu'à son retraitement. Dès que vous retraitez le modèle, la prédiction change pour utiliser à la fois ARIMA et ARTXP.  
  
 Par conséquent, si vous souhaitez éviter de modifier le modèle, vous devez parcourir uniquement le modèle sans jamais le traiter. Vous pouvez également définir explicitement les paramètres FORECAST_METHOD ou PREDICTION_SMOOTHING.  
  
 Pour plus d’informations sur la configuration des modèles mixtes, consultez [Références techniques relatives à l’algorithme MTS (Microsoft Time Series)](microsoft-time-series-algorithm-technical-reference.md).  
  
 Si le fournisseur utilisé pour la source de données du modèle est SQL Server ou le fournisseur de données SQL Client 10, vous devez aussi modifier la définition de la source de données pour spécifier la version antérieure de SQL Server Native Client. Sinon, [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] génère une erreur indiquant que le fournisseur n'est pas enregistré.  
  
##  <a name="deploying-models-with-holdout"></a><a name="bkmk_Holdout"></a>Déploiement de modèles avec exclusion  
 Si vous utilisez [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] pour créer une structure d'exploration de données qui contient une partition d'exclusion utilisée pour tester les modèles d'exploration de données, la structure d'exploration de données peut être déployée sur une instance de SQL Server 2005, mais les informations de partition seront perdues.  
  
 Lorsque vous ouvrez la structure d'exploration de données dans SQL Server 2005 Analysis Services, [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] génère une erreur, puis régénère la structure pour supprimer la partition d'exclusion.  
  
 Une fois la structure régénérée, la taille de la partition exclusion n’est plus disponible dans le Fenêtre Propriétés ; Toutefois, la valeur \<Ddl100_100 : HoldoutMaxPercent>30\</ddl100_100 : HoldoutMaxPercent>) peut toujours être présente dans le fichier de script ASSL.  
  
##  <a name="deploying-models-with-filters"></a><a name="bkmk_Filter"></a>Déploiement de modèles avec des filtres  
 Si vous utilisez [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] pour appliquer un filtre à un modèle d'exploration de données, le modèle peut être déployé sur une instance de SQL Server 2005, mais le filtre ne sera pas appliqué.  
  
 Lorsque vous ouvrez le modèle d'exploration de données, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] génère une erreur, puis régénère le modèle pour supprimer le filtre.  
  
##  <a name="restoring-from-database-backups"></a><a name="bkmk_Backup"></a>Restauration à partir de sauvegardes de bases de données  
 Vous ne pouvez pas restaurer une sauvegarde de base de données créée dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] vers une instance de SQL Server 2005. Si vous le faites, SQL Server Management Studio génère une erreur.  
  
 Si vous créez une sauvegarde d'une base de données SQL Server 2005 Analysis Services et restaurez cette sauvegarde sur une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], tous les modèles de séries chronologiques sont modifiés comme indiqué dans la section précédente.  
  
##  <a name="using-database-synchronization"></a><a name="bkmk_Synch"></a>Utilisation de la synchronisation de base de données  
 La synchronisation de base de données n'est pas prise en charge de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] vers SQL Server 2005.  
  
 Si vous essayez de synchroniser une base de données [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , le serveur retourne une erreur et la synchronisation de la base de données échoue.  
  
## <a name="see-also"></a>Voir aussi  
 [Compatibilité descendante Analysis Services](../analysis-services-backward-compatibility.md)  
  
  
