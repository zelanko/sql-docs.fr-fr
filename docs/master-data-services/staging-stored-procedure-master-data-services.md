---
title: "Proc&#233;dure stock&#233;e de mise en lots (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "04/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
caps.latest.revision: 15
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 15
---
# Proc&#233;dure stock&#233;e de mise en lots (Master Data Services)
  Lors de l’initialisation du processus de site à partir de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], vous devez utiliser l’une des trois procédures stockées.  
  
-   stg.udp_\<nom>_Feuille  
  
-   stg.udp_\<nom>_Consolidé  
  
-   stg.udp_\<nom>_Relation  
  
 Où nom indique le nom de la table de mise en lots spécifié lors de la création de l'entité.  
  
## Paramètres de procédure stockée du processus de site  
 Le tableau suivant répertorie les paramètres de ces procédures stockées.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**VersionName**<br /><br /> Requis|Nom de la version. Peut ou non respecter la casse, en fonction de votre paramètre de classement [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|  
|**LogFlag**<br /><br /> Requis|Détermine si les transactions sont inscrites dans un journal au cours du processus de site. Les valeurs possibles sont :<br /><br /> **0** : ne pas enregistrer les transactions.<br /><br /> **1** : enregistrer les transactions.<br /><br /> <br /><br /> Pour plus d’informations sur les transactions, consultez [Transactions &#40;Master Data Services&#41;](../master-data-services/transactions-master-data-services.md).|  
|**BatchTag**<br /><br /> Requis, sauf par le service Web|La valeur de **BatchTag** spécifiée dans la table de mise en lots.|  
|**Batch_ID**<br /><br /> Requis par le service Web uniquement|La valeur de **Batch_ID** spécifiée dans la table de mise en lots.|  
|**Nom d'utilisateur**|Paramètre facultatif :|  
|**ID d'utilisateur**|Paramètre facultatif :|  
  
### Exemple de procédure stockée du processus de site  
 L'exemple suivant montre comment démarrer le processus de site à l'aide de la procédure stockée de mise en lots.  
  
```  
USE [DATABASE_NAME]  
GO  
  
EXEC[stg].[udp_name_Leaf]  
      @VersionName = N'VERSION_1',  
@LogFlag = 1,  
@BatchTag = N'batch1'  
      @UserName=N’domain\user’  
  
GO  
  
```  
  
## Voir aussi  
 [Procédure stockée de validation &#40;Master Data Services&#41;](../master-data-services/validation-stored-procedure-master-data-services.md)   
 [Afficher les erreurs rencontrées lors de la mise en lots &#40;Master Data Services&#41;](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md)  
  
  