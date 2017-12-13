---
title: Options de restauration | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- databases [Analysis Services], restoring
- restoring databases [Analysis Services]
ms.assetid: 75c73802-f321-4671-afc7-54505d62c013
caps.latest.revision: "23"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e47fb9f30ca2a6f3156d3ef4fb70565f31183a65
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="restore-options"></a>Options de restauration
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Il existe plusieurs façons pour restaurer votre [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bases de données, qui nécessitent que vous disposez des autorisations d’administrateur pour l’ordinateur du serveur et le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données. Pour restaurer une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vous pouvez ouvrir la boîte de dialogue **Restaurer la base de données** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], sélectionner la configuration des options appropriée, puis exécuter la restauration à partir de cette boîte de dialogue. Ou bien, vous pouvez créer un script utilisant les paramètres déjà spécifiés dans le fichier ; ce script peut ensuite être enregistré et exécuté aussi souvent que nécessaire. De cette façon, la restauration est effectuée en utilisant XMLA, comme le décrit la section suivante.  
  
## <a name="restoring-databases-using-xmla"></a>Restauration de bases de données à l'aide de XMLA  
 La commande XMLA Restore permet d'automatiser le processus de restauration en exécutant une restauration basée sur un fichier .abf. La commande Restore possède des propriétés qu'il est possible de définir pour spécifier des définitions de sécurité, l'emplacement où stocker les partitions distantes et le déplacement d'objets ROLAP (OLAP relationnel). Pour plus d’informations, consultez [Élément Restore &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md).  
  
> [!IMPORTANT]  
>  Pour chaque fichier de sauvegarde, l'utilisateur qui exécute la commande de restauration doit avoir l'autorisation de lire à partir de l'emplacement de sauvegarde spécifié pour chaque fichier. Pour restaurer une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui n'est pas installée sur le serveur, l'utilisateur doit également être un membre du rôle serveur pour cette instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Pour remplacer une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , l’utilisateur doit avoir l’un des rôles suivants : membre du rôle serveur pour l’instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou membre d’un rôle de base de données avec les autorisations de contrôle total (Administrateur) sur la base de données à restaurer.  
  
> [!NOTE]  
>  Après la restauration d'une base de données existante, l'utilisateur qui a restauré la base de données peut perdre l'accès à la base de données restaurée. Cette perte d'accès peut se produire si, au moment de la sauvegarde, l'utilisateur n'était pas un membre du rôle de serveur ou un membre du rôle de base de données avec les autorisations de contrôle total (Administrateur).  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue Restaurer la base de données &#40;Analysis Services - Données multidimensionnelles&#41;](http://msdn.microsoft.com/library/a3990d47-55e2-424e-8eac-87edc937e806)   
 [Sauvegarde et restauration de bases de données Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)   
 [Restaurer l’élément &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Sauvegarde, restauration et synchronisation de bases de données &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
