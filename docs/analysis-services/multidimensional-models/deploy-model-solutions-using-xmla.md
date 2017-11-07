---
title: "Déployer des Solutions de modèle à l’aide de XMLA | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML scripts [Analysis Services]
- scripts [Analysis Services], deployment
- deploying [Analysis Services], XML scripts
- Analysis Services deployments, XML scripts
ms.assetid: a8cb1837-fcac-4730-bea4-a72cf94d9f7c
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b8315642255f95211c8e9bc2fd7e540351cdd3fb
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="deploy-model-solutions-using-xmla"></a>Déployer des solutions de modèle à l'aide de XMLA
  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], l’option **CREATE To** de la commande **Générer un script de la base de données en tant que** crée un script XML d’une base de données [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] entière ou de l’un de ses objets. Le script résultant peut être exécuté sur un autre ordinateur pour recréer le schéma (métadonnées) de la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Le script génère l'ensemble de la base de données, et il n'existe aucun mécanisme pour mettre à jour de manière incrémentielle les objets déjà déployés lors de l'utilisation du script. Après l'exécution du script et le déploiement de la base de données, la nouvelle base de données doit être traitée pour que les utilisateurs puissent l'utiliser.  
  
 Pour plus d’informations sur la commande **Générer un script de la base de données en tant que** , consultez [Documenter et générer des scripts pour une base de données Analysis Services](../../analysis-services/multidimensional-models/document-and-script-an-analysis-services-database.md).  
  
## <a name="modifying-object-properties-in-the-xml-script"></a>Modification des propriétés des objets dans le script XML  
 Quand vous utilisez la commande **Générer un script de la base de données en tant que** , vous ne pouvez pas modifier des propriétés spécifiques (telles que le nom de la base de données, les chaînes de connexion à la source de données et les paramètres de sécurité) des objets de la base de données. Ces propriétés doivent être modifiées manuellement dans le script après sa génération, ou dans la base de données déployée après l'exécution du script.  
  
> [!IMPORTANT]  
>  Le script XML ne contient pas le mot de passe si celui-ci est spécifié dans la chaîne de connexion d'une source de données ou à des fins d'emprunt d'identité. Dans la mesure où le mot de passe est nécessaire à des fins de traitement dans ce scénario, vous devez l'ajouter manuellement au script XML avant son exécution ou après l'exécution du script XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Deploy Model Solutions Using the Deployment Wizard](../../analysis-services/multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md)   
 [Synchroniser des base de données Analysis Services](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)  
  
  

