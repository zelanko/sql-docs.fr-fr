---
title: Interdit les Types et membres dans System.Data.dll | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: reference
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: ee5f55e9-fbef-401a-be18-a2e5873c8720
caps.latest.revision: 17
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 29077d49a290e37abd205d30e3e3ffa5102d6406
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2018
ms.locfileid: "35696760"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a>Types et membres dans System.Data.dll interdits
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] common language integration (CLR) programming disallows the use of a type or member that has a **HostProtectionAttribute** that specifies a **System.Security.Permissions.HostProtectionResource** enumeration with a value of **ExternalProcessMgmt**, **ExternalThreading**, **MayLeakOnAbort**, **SecurityInfrastructure**, **SelfAffectingProcessMgmnt**, **SelfAffectingThreading**, **SharedState**, **Synchronization**, or **UI**. Le tableau suivant répertorie les membres et les types de l'assembly System.Data dll dont les valeurs d'attribut de protection de l'hôte (HPA) sont interdites.  
  
> [!NOTE]  
>  Cette liste a été générée à partir des assemblys pris en charge. Pour plus d’informations, consultez [prise en charge des bibliothèques .NET Framework](../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
|Type ou membre|Valeur(s) HPA|  
|--------------------|--------------------|  
|System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery()|ExternalThreading|  
|System.Data.SqlClient.SqlCommand.BeginExecuteReader()|ExternalThreading|  
|System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency..ctor()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency.Start()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency.Stop()|ExternalThreading|  
|System.Data.TypedDataSetGenerator|SharedState, Synchronization|  
|System.Xml.XmlDataDocument|Synchronization|  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs de Protection d’hôte et de la programmation de l’intégration CLR](../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Types et membres dans Microsoft.VisualBasic.dll interdits](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [Types et membres dans mscorlib.dll interdits](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-mscorlib-dll.md)   
 [Types et membres dans System.dll interdits](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-dll.md)   
 [Types et membres non autorisés dans System.Core.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-core-dll.md)  
  
  
