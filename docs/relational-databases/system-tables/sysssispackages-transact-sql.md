---
title: sysssispackages (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdtspackages90_TSQL
- sysdtspackages90
dev_langs:
- TSQL
helpviewer_keywords:
- sysssispackages system table
ms.assetid: 66155dcd-dcdb-4e33-a242-1625828ad8d2
caps.latest.revision: 43
author: douglasl
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1143dc7897d5725279c2146d295bb5146fcc628c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="sysssispackages-transact-sql"></a>sysssispackages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque package est enregistré dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette table est stockée dans le **msdb** base de données.  
  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Identificateur unique du package.|  
|**id**|**uniqueidentifier**|GUID du package.|  
|**description**|**nvarchar**|Description facultative du package.|  
|**createdate**|**datetime**|Date de que création du package.|  
|**folderId**|**uniqueidentifier**|GUID du dossier logique dans lequel [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] répertorie le package.|  
|**ownersid**|**varbinary**|Identificateur de sécurité unique de l'utilisateur qui a créé le package.|  
|**packagedata**|**image**|Package.|  
|**packageformat**|**int**|Format dans lequel le package est enregistré :<br /><br /> La valeur 2 indique que le package est enregistré dans le [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] format.<br /><br /> La valeur 3 indique que le package est enregistré au format de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]ou version ultérieure.|  
|**packagetype**|**int**|Client à l'origine du package. Les valeurs possibles sont les suivantes :<br /><br /> 0 (valeur par défaut)<br /><br /> 1 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Importation et exportation)<br /><br /> 3 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] réplication)<br /><br /> 5 ([!INCLUDE[ssIS](../../includes/ssis-md.md)] concepteur)<br /><br /> 6 (Assistant ou Concepteur de plan de maintenance).<br /><br /> <br /><br /> Notez que les valeurs de cette colonne correspondent à la <xref:Microsoft.SqlServer.Dts.Runtime.DTSPackageType> énumération.|  
|**VerMajor**|**int**|Dernière version majeure du package.|  
|**VerMinor**|**int**|Dernière version mineure du package.|  
|**verbuild**|**int**|Dernière build du package.|  
|**vercomments**|**nvarchar**|Commentaires sur la version du package.|  
|**Verid**|**uniqueidentifier**|Le GUID de la version du package.|  
|**IsEncrypted**|**bit**|Valeur booléenne qui indique si le package est chiffré.|  
|**readrolesid**|**varbinary**|Rôle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui peut charger des packages.|  
|**writerolesid**|**varbinary**|Rôle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui peut enregistrer des packages.|  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services & #40 ; SSIS & #41 ; Packages](../../integration-services/integration-services-ssis-packages.md)  
  
  
