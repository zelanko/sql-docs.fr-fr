---
title: "(Master Data Services) de procédure stockée de validation | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 332d3c86-4440-4f12-a6cb-ffbfbccde52c
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4c0606a05973dfbcd8e43f24898c8a9ce01d9fc8
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="validation-stored-procedure-master-data-services"></a>Procédure stockée de validation (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], validez une version pour appliquer des règles d’entreprise à tous les membres dans la version de modèle.  
  
 Cette rubrique explique comment utiliser la procédure stockée **mdm.udpValidateModel** pour valider des données. Si vous êtes administrateur dans l’application web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , vous pouvez à la place effectuer la validation dans l’interface utilisateur. Pour plus d’informations, consultez [Validate a Version against Business Rules &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md).  
  
> [!NOTE]  
>  Si vous appelez la validation avant la fin de l'exécution du processus de site, les membres qui n'ont pas terminé la mise en lots ne sont pas validés.  
  
## <a name="example"></a>Exemple  
  
```  
DECLARE @ModelName nVarchar(50) = 'Customer'   
DECLARE @Model_id int   
DECLARE @UserName nvarchar(50)= 'DOMAIN\user_name'   
DECLARE @User_ID int   
DECLARE @Version_ID int   
  
SET @User_ID = (SELECT ID    
                 FROM mdm.tblUser u   
                 WHERE u.UserName = @UserName)   
SET @Model_ID = (SELECT Top 1 Model_ID   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_Name = @ModelName)   
SET @Version_ID = (SELECT MAX(ID)   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_ID = @Model_ID)  
  
EXECUTE mdm.udpValidateModel @User_ID, @Model_ID, @Version_ID, 1  
  
```  
  
## <a name="parameters"></a>Paramètres  
 Cette procédure présente les paramètres suivants :  
  
|Paramètre|Description|  
|---------------|-----------------|  
|UserID|Identificateur utilisateur.|  
|Model_ID|ID de modèle.|  
|Version_ID|ID de version.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble : importation de données à partir de tables &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [Valider une Version par rapport aux règles d’entreprise &#40; Master Data Services &#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
  
