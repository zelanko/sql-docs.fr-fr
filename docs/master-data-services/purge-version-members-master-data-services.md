---
title: Purge des membres de version (Master Data Services) | Microsoft Docs
ms.custom: SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: adecce2d-46bb-49ff-8be9-0b31b8dd3cb6
caps.latest.revision: "7"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3df9f832b7e19c394cd8bcbb1c6c2e8903e2deaa
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="purge-version-members-master-data-services"></a>Purge des membres de version [Master Data Services]
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], la suppression d’un membre n’a pour effet que de le désactiver (suppression réversible). Les données se trouvent toujours dans la base de données. Cette rubrique explique comment purger (supprimer définitivement) tous les membres supprimés de manière réversible dans une version de modèle.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle Gestion des versions.  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
## <a name="to-purge-soft-deleted-members"></a>Pour purger les membres supprimés de manière réversible  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Gestion des versions**.  
  
2.  Sur la page **Gérer les versions** , sélectionnez le modèle associé à la version que vous souhaitez purger. La liste des versions de modèle s’affiche.  
  
3.  Sélectionnez la ligne de la version à purger.  
  
4.  Cliquez sur **Purger les membres**.  
  
5.  À l’invite de confirmation, cliquez sur « OK ».  
  
## <a name="additional-methods-to-purge-members"></a>Autres méthodes de purge  
 Une purge des membres de version a pour effet de supprimer définitivement les membres qui ont été supprimés de manière réversible dans toutes les entités appartenant à la version sélectionnée. Une autre solution consiste à utiliser une mise en lots de la base d’entités pour supprimer définitivement les membres spécifiques d’une entité uniquement. En outre, les administrateurs d’entités ayant une autorisation de fonction Explorateur peuvent purger une version de l’entité sur la page de l’explorateur d’entités.  
  
 Pour plus d’informations, consultez [Table de mise en lots des membres feuilles &#40;Master Data Services&#41;](../master-data-services/leaf-member-staging-table-master-data-services.md).  
  
  
