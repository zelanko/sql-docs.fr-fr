---
title: Options de restauration | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], restoring
- restoring databases [Analysis Services]
ms.assetid: 75c73802-f321-4671-afc7-54505d62c013
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1a66aabc9388c85e8d7d1e3df26bc02388347b6a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62736650"
---
# <a name="restore-options"></a>Options de restauration
  Quelle que soit la méthode choisie pour restaurer vos bases de données [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vous devez avoir des autorisations d’administrateur pour le serveur et la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Pour restaurer une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vous pouvez ouvrir la boîte de dialogue **Restaurer la base de données** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], sélectionner la configuration des options appropriée, puis exécuter la restauration à partir de cette boîte de dialogue. Ou bien, vous pouvez créer un script utilisant les paramètres déjà spécifiés dans le fichier ; ce script peut ensuite être enregistré et exécuté aussi souvent que nécessaire. De cette façon, la restauration est effectuée en utilisant XMLA, comme le décrit la section suivante.  
  
## <a name="restoring-databases-using-xmla"></a>Restauration de bases de données à l'aide de XMLA  
 La commande XMLA Restore permet d'automatiser le processus de restauration en exécutant une restauration basée sur un fichier .abf. La commande Restore possède des propriétés qu'il est possible de définir pour spécifier des définitions de sécurité, l'emplacement où stocker les partitions distantes et le déplacement d'objets ROLAP (OLAP relationnel). Pour plus d’informations, consultez [Restore Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla).  
  
> [!IMPORTANT]  
>  Pour chaque fichier de sauvegarde, l'utilisateur qui exécute la commande de restauration doit avoir l'autorisation de lire à partir de l'emplacement de sauvegarde spécifié pour chaque fichier. Pour restaurer une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui n'est pas installée sur le serveur, l'utilisateur doit également être un membre du rôle serveur pour cette instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Pour remplacer une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , l’utilisateur doit avoir l’un des rôles suivants : membre du rôle serveur pour l’instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou membre d’un rôle de base de données avec les autorisations de contrôle total (Administrateur) sur la base de données à restaurer.  
  
> [!NOTE]  
>  Après la restauration d'une base de données existante, l'utilisateur qui a restauré la base de données peut perdre l'accès à la base de données restaurée. Cette perte d'accès peut se produire si, au moment de la sauvegarde, l'utilisateur n'était pas un membre du rôle de serveur ou un membre du rôle de base de données avec les autorisations de contrôle total (Administrateur).  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue Restaurer la base de données &#40;Analysis Services - Données multidimensionnelles&#41;](../restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Sauvegarde et restauration de bases de données Analysis Services](backup-and-restore-of-analysis-services-databases.md)   
 [Élément Restore &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla)   
 [Sauvegarde, restauration et synchronisation de bases de données &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
