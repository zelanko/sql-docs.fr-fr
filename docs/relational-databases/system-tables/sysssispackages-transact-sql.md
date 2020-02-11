---
title: sysssispackages (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdtspackages90_TSQL
- sysdtspackages90
dev_langs:
- TSQL
helpviewer_keywords:
- sysssispackages system table
ms.assetid: 66155dcd-dcdb-4e33-a242-1625828ad8d2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 21487ba46e53997ebb50403cc4eaf1ae54f0a103
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68029644"
---
# <a name="sysssispackages-transact-sql"></a>sysssispackages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque package enregistré dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette table est stockée dans la base de données **msdb** .  
  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nomme**|**sysname**|Identificateur unique du package.|  
|**identifi**|**uniqueidentifier**|GUID du package.|  
|**description**|**nvarchar**|Description facultative du package.|  
|**création**|**DATETIME**|Date à laquelle le package a été créé.|  
|**FolderId**|**uniqueidentifier**|GUID du dossier logique dans lequel [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] répertorie le package.|  
|**ownersid**|**varbinary**|Identificateur de sécurité unique de l'utilisateur qui a créé le package.|  
|**packagedata**|**image**|Package.|  
|**packageformat**|**int**|Format dans lequel le package est enregistré :<br /><br /> La valeur 2 indique que le package est enregistré [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] au format.<br /><br /> La valeur 3 indique que le package est enregistré au format [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]ou version ultérieure.|  
|**PackageType**|**int**|Client à l'origine du package. Les valeurs possibles sont les suivantes :<br /><br /> 0 (valeur par défaut)<br /><br /> 1 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant importation et exportation)<br /><br /> 3 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] réplication)<br /><br /> 5 ([!INCLUDE[ssIS](../../includes/ssis-md.md)] concepteur)<br /><br /> 6 (Assistant ou Concepteur de plan de maintenance).<br /><br /> <br /><br /> Notez que les valeurs de cette colonne correspondent à l' <xref:Microsoft.SqlServer.Dts.Runtime.DTSPackageType> énumération.|  
|**vermajor**|**int**|Dernière version majeure du package.|  
|**verminor**|**int**|Dernière version mineure du package.|  
|**verbuild**|**int**|Dernière build du package.|  
|**vercomments**|**nvarchar**|Commentaires sur la version du package.|  
|**verid**|**uniqueidentifier**|GUID de la version du package.|  
|**IsEncrypted**|**bit**|Valeur booléenne qui indique si le package est chiffré.|  
|**readrolesid**|**varbinary**|Rôle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui peut charger des packages.|  
|**writerolesid**|**varbinary**|Rôle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui peut enregistrer des packages.|  
  
## <a name="see-also"></a>Voir aussi  
 [Packages Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-packages.md)  
  
  
