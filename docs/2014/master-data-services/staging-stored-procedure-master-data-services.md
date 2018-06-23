---
title: Procédure stockée de mise en lots (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1ab4d483a41c64a97d320711c6f46bf6831ea078
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039329"
---
# <a name="staging-stored-procedure-master-data-services"></a>Procédure stockée de mise en lots (Master Data Services)
  Lors de l’initialisation du processus de site à partir de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], vous devez utiliser l’une des trois procédures stockées.  
  
-   stg.udp_name_Leaf  
  
-   stg.udp_name_Consolidated  
  
-   stg.udp_name_Relationship  
  
 Où nom indique le nom de la table de mise en lots spécifié lors de la création de l'entité.  
  
## <a name="staging-process-stored-procedure-parameters"></a>Paramètres de procédure stockée du processus de site  
 Le tableau suivant répertorie les paramètres de ces procédures stockées.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**VersionName**<br /><br /> Requis|Nom de la version. Peut ou non respecter la casse, en fonction de votre paramètre de classement [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|  
|**LogFlag**<br /><br /> Requis|Détermine si les transactions sont inscrites dans un journal au cours du processus de site. Les valeurs possibles sont :<br /><br /> **0**: ne pas enregistrer les transactions.<br />**1** : enregistrer les transactions.<br /><br /> <br /><br /> Pour plus d’informations sur les transactions, consultez [Transactions &#40;Master Data Services&#41;](transactions-master-data-services.md).|  
|**BatchTag**<br /><br /> Requis, sauf par le service Web|La valeur de **BatchTag** spécifiée dans la table de mise en lots.|  
|**Batch_ID**<br /><br /> Requis par le service Web uniquement|La valeur de **Batch_ID** spécifiée dans la table de mise en lots.|  
  
### <a name="staging-process-stored-procedure-example"></a>Exemple de procédure stockée du processus de site  
 L'exemple suivant montre comment démarrer le processus de site à l'aide de la procédure stockée de mise en lots.  
  
```  
USE [DATABASE_NAME]  
GO  
  
EXEC[stg].[udp_name_Leaf]  
      @VersionName = N'VERSION_1',  
@LogFlag = 1,  
@BatchTag = N'batch1'  
  
GO  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure stockée de validation &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md)   
 [Charger ou mettre à jour des membres dans Master Data Services à l’aide du processus de site](/sql/2014/master-data-services/add-update-and-delete-data-master-data-services)   
 [Afficher les erreurs qui se produisent pendant le processus de mise en lots &#40;Master Data Services&#41;](view-errors-that-occur-during-staging-master-data-services.md)  
  
  
