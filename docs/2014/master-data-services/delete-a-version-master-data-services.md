---
title: Supprimer une version (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], deleting
- deleting versions [Master Data Services]
ms.assetid: 2a4eeffe-8379-4744-ad44-c27d8c8ac9a8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 63f0f2f1b55bbb56b17357d58404815af496ac49
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48205439"
---
# <a name="delete-a-version-master-data-services"></a>Supprimer une version (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], supprimez une version lorsque vous êtes sûr de ne plus avoir besoin des données de référence qui lui sont associées. Après avoir supprimé une version, vous ne pouvez pas récupérer les données de référence associées.  
  
> [!WARNING]  
>  Si un modèle a une seule version et que vous la supprimez, le modèle devient inutilisable.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'afficher la vue mdm.viw_SYSTEM_SCHEMA_VERSION et d'exécuter la procédure stockée mds.udpVersionDelete dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Pour plus d’informations, consultez [Sécurité de l’objet de base de données &#40;Master Data Services&#41;](database-object-security-master-data-services.md).  
  
### <a name="to-delete-a-version"></a>Pour supprimer une version  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] et connectez-vous à l’instance [!INCLUDE[ssDE](../includes/ssde-md.md)] pour votre base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Ouvrez la vue mdm.viw_SYSTEM_SCHEMA_VERSION.  
  
3.  Recherchez la version du modèle que vous souhaitez supprimer et copiez la valeur dans le champ **ID** .  
  
4.  Créez une requête.  
  
5.  Tapez le texte suivant, en remplaçant *ID_version* par la valeur copiée à l’étape 2.  
  
    ```  
    EXEC [mdm].[udpVersionDelete] @Version_ID='version_ID'  
    ```  
  
6.  Exécute la requête.  
  
    > [!NOTE]  
    >  Vous devrez peut-être attendre quelques minutes avant que l'application Web ne reflète la modification.  
  
## <a name="see-also"></a>Voir aussi  
 [Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)   
 [Copier une Version &#40;Master Data Services&#41;](../../2014/master-data-services/copy-a-version-master-data-services.md)  
  
  
