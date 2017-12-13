---
title: "Modifier ou supprimer une base de données Analysis Services | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- databases [Analysis Services], modifying
- removing databases
- deleting databases
- dropping databases
- databases [Analysis Services], deleting
- modifying databases
ms.assetid: e48e3988-c091-4379-aabc-4da62f709a7e
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 41cb7d7f1c2da7ef2664de3e41c17613019094d6
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="modify-or-delete-an-analysis-services-database"></a>Modifier ou supprimer une base de données Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Vous pouvez modifier le nom et la description d’un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données avant le déploiement dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] et après le déploiement dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Vous pouvez également régler des paramètres supplémentaires sur une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , en fonction de l'environnement.  
  
> [!NOTE]  
>  Vous ne pouvez pas modifier les propriétés de base de données à l'aide de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] en mode en ligne.  
  
## <a name="modifying-databases-using-sql-server-management-studio"></a>Modification des bases de données à l'aide de SQL Server Management Studio  
 Une fois qu'une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] a été déployée, vous pouvez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour modifier le mode d'emprunt d'identité utilisé par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] lors de la connexion à des sources de données incluses dans la base de données. Le mode d'emprunt d'identité vous permet de spécifier le contexte de sécurité utilisé par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] lors d'une tentative de connexion à une source de données pour des tâches de traitement, de navigation ou d'extraction.  
  
## <a name="modifying-databases-using-sql-server-data-tools"></a>Modification des bases de données à l'aide des outils de données SQL Server  
 Vous pouvez utiliser [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] en mode projet pour modifier les traductions de la légende et de la description d’un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilisé pour définir une base de données. Pour plus d’informations sur l’utilisation de traductions dans une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , consultez [Scénarios de globalisation pour Analysis Services](../../analysis-services/globalization-scenarios-for-analysis-services.md).  
  
 Vous pouvez également définir les alias et les fonctions d'agrégation associés aux types de comptes utilisés par les attributs de compte dans les dimensions incluses dans la base de données. Les alias vous permettent de sélectionner la terminologie d'entreprise utilisée par votre organisation pour les types de comptes dans un plan comptable. Les types de comptes sont utilisés par les membres d'un attribut de compte pour indiquer comment agréger les mesures sur chaque membre en utilisant les fonctions d'agrégation spécifiées pour chaque type de compte inclus dans la base de données. Pour plus d’informations sur les attributs de compte, consultez [Attributs et hiérarchies d’attributs](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).  
  
## <a name="deleting-databases"></a>suppression de bases de données  
 La suppression d'une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] existante entraîne la suppression de la base de données et de tous les cubes, dimensions et modèles d'exploration de données inclus dans la base de données. Vous pouvez supprimer uniquement une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] existante dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-delete-an-analysis-services-database"></a>Pour supprimer une base de données Analysis Services  
  
1.  Connectez-vous à une instance d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2.  Dans **l’Explorateur d’objets**, développez le nœud de l’instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connectée et vérifiez que l’objet à supprimer est visible.  
  
3.  Cliquez avec le bouton droit sur l’objet à supprimer et sélectionnez **Supprimer**.  
  
4.  Dans la boîte de dialogue **Supprimer l'objet** , cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Documenter et générer des scripts pour une base de données Analysis Services](../../analysis-services/multidimensional-models/document-and-script-an-analysis-services-database.md)  
  
  
