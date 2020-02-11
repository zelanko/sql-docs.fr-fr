---
title: Procédure stockée de mise en lots
ms.custom: ''
ms.date: 04/01/2016
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 103c43f012f6cf7025139fd29656a42d00fc233f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73727886"
---
# <a name="staging-stored-procedure-master-data-services"></a>Procédure stockée de mise en lots (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Lors de l’initialisation du processus de site à partir de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], vous devez utiliser l’une des trois procédures stockées.  
  
-   stg.udp_\<nom>_Leaf  
  
-   stg.udp_\<nom>_Consolidated  
  
-   stg.udp_\<nom>_Relationship  
  
 Où nom indique le nom de la table de mise en lots spécifié lors de la création de l'entité.  
  
## <a name="staging-process-stored-procedure-parameters"></a>Paramètres de procédure stockée du processus de site  
 Le tableau suivant répertorie les paramètres de ces procédures stockées.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**VersionName**<br /><br /> Obligatoire|Nom de la version. Peut ou non respecter la casse, en fonction de votre paramètre de classement [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|  
|**LogFlag**<br /><br /> Obligatoire|Détermine si les transactions sont inscrites dans un journal au cours du processus de site. Les valeurs possibles sont :<br /><br /> **0**: ne pas enregistrer les transactions.<br /><br /> **1**: enregistrer les transactions.<br /><br /> <br /><br /> Pour plus d’informations sur les transactions, consultez [Transactions &#40;Master Data Services&#41;](../master-data-services/transactions-master-data-services.md).|  
|**BatchTag**<br /><br /> Requis, sauf par le service Web|La valeur de **BatchTag** spécifiée dans la table de mise en lots.|  
|**Batch_ID**<br /><br /> Requis par le service Web uniquement|La valeur de **Batch_ID** spécifiée dans la table de mise en lots.|  
|**Nom d’utilisateur**|Paramètre facultatif :|  
|**ID d'utilisateur**|Paramètre facultatif :|  
  
### <a name="staging-process-stored-procedure-example"></a>Exemple de procédure stockée du processus de site  
 L'exemple suivant montre comment démarrer le processus de site à l'aide de la procédure stockée de mise en lots.  
  
```  
USE [DATABASE_NAME]  
GO  
  
EXEC[stg].[udp_name_Leaf]  
      @VersionName = N'VERSION_1',  
@LogFlag = 1,  
@BatchTag = N'batch1'  
      @UserName=N'domain\user'  
  
GO  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [&#40;de la procédure stockée de validation Master Data Services&#41;](../master-data-services/validation-stored-procedure-master-data-services.md)   
 [Afficher les erreurs qui se produisent lors de la &#40;de la mise en lots Master Data Services&#41;](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md)  
  
  
