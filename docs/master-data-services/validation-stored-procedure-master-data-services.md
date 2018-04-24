---
title: Procédure stockée de validation (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 332d3c86-4440-4f12-a6cb-ffbfbccde52c
caps.latest.revision: 8
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b4e39072255740f05ee0709f732caeb00188bf83
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="validation-stored-procedure-master-data-services"></a>Procédure stockée de validation (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], validez une version pour appliquer des règles d’entreprise à tous les membres dans la version de modèle.  
  
 Cette rubrique explique comment utiliser la procédure stockée **mdm.udpValidateModel** pour valider des données. Si vous êtes administrateur dans l’application web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , vous pouvez à la place effectuer la validation dans l’interface utilisateur. Pour plus d’informations, consultez [Valider une version par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md).  
  
> [!NOTE]  
>  Si vous appelez la validation avant la fin de l'exécution du processus de site, les membres qui n'ont pas terminé la mise en lots ne sont pas validés.  
  
## <a name="example"></a> Exemple  
  
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
  
## <a name="see-also"></a> Voir aussi  
 [Vue d’ensemble : importation de données à partir de tables &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [Valider une version par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
  
