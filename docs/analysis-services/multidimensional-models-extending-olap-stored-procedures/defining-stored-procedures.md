---
title: "Définition de procédures stockées | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- stored procedures [Analysis Services]
- OLAP [Analysis Services], stored procedures
- external routines [Analysis Services]
- stored procedures [Analysis Services], about stored procedures
ms.assetid: f9c57d91-f60f-4f0e-8f7f-d87f4ba97b7c
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: af5d0ffc0b7aaa1b03ca4166d59667692566b036
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="defining-stored-procedures"></a>Définition de procédures stockées
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Vous pouvez utiliser des procédures stockées pour appeler des routines externes à partir de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Vous pouvez écrire les routines externes appelées par une procédure stockée dans n'importe quel langage CLR (Common Language Runtime), comme C, C++, C#, Visual Basic ou Visual Basic .NET. Une procédure stockée peut être créée une fois et être ensuite appelée à partir de nombreux contextes, par exemple par d'autres procédures stockées, par des mesures calculées ou par des applications clientes. Les procédures stockées simplifient le développement et l'implémentation des bases de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en permettant de développer une fois du code commun et de le stoker dans un emplacement unique. Les procédures stockées peuvent être utilisées pour ajouter à vos applications des fonctionnalités métier qui ne sont pas fournies par les fonctionnalités natives de MDX.  
  
 Cette section contient les informations nécessaires pour comprendre, concevoir et mettre en œuvre des procédures stockées.  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[Conception de procédures stockées](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/designing-stored-procedures.md)|Explique comment concevoir des assemblys pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Création de procédures stockées](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/creating-stored-procedures.md)|Explique comment créer des assemblys pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Appel de procédures stockées](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/calling-stored-procedures.md)|Fournit des informations sur l'utilisation des assemblys dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Accès au contexte de requête dans les procédures stockées](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/accessing-query-context-in-stored-procedures.md)|Explique comment accéder aux informations d'étendue et de contexte avec des assemblys.|  
|[Définition de la sécurité des procédures stockées](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/setting-security-for-stored-procedures.md)|Explique comment configurer la sécurité des assemblys dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Débogage de procédures stockées](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/debugging-stored-procedures.md)|Explique comment déboguer les assemblys dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys de modèle multidimensionnel](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
