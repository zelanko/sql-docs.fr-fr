---
title: Types et membres interdits dans System.Data.dll | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: ee5f55e9-fbef-401a-be18-a2e5873c8720
author: rothja
ms.author: jroth
ms.openlocfilehash: 6417dfbe000a3c149df8abe80d1fe3b961fc08cf
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84954254"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a>Types et membres non autorisés dans System.Data.dll
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]la programmation CLR (Common Language Integration) interdit l’utilisation d’un type ou d’un membre ayant un `HostProtectionAttribute` qui spécifie une `System.Security.Permissions.HostProtectionResource` énumération avec la valeur `ExternalProcessMgmt` , `ExternalThreading` ,, `MayLeakOnAbort` `SecurityInfrastructure` , `SelfAffectingProcessMgmnt` , `SelfAffectingThreading` , **SharedState**, `Synchronization` ou `UI` . Le tableau suivant répertorie les membres et les types de l'assembly System.Data dll dont les valeurs d'attribut de protection de l'hôte (HPA) sont interdites.  
  
> [!NOTE]  
>  Cette liste a été générée à partir des assemblys pris en charge. Pour plus d’informations, consultez [.NET Framework les bibliothèques prises en charge](../clr-integration/database-objects/supported-net-framework-libraries.md).  
  
|Type ou membre|Valeur(s) HPA|  
|--------------------|--------------------|  
|System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery()|ExternalThreading|  
|System.Data.SqlClient.SqlCommand.BeginExecuteReader()|ExternalThreading|  
|System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency..ctor()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency.Start()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency.Stop()|ExternalThreading|  
|System.Data.TypedDataSetGenerator|SharedState, Synchronization|  
|System.Xml.XmlDataDocument|Synchronisation|  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs de protection de l’hôte et programmation de l’intégration du CLR](host-protection-attributes-and-clr-integration-programming.md)   
 [Types et membres interdits dans Microsoft.VisualBasic.dll](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [Types et membres interdits dans mscorlib.dll](disallowed-types-and-members-in-mscorlib-dll.md)   
 [Types et membres interdits dans System.dll](disallowed-types-and-members-in-system-dll.md)   
 [Types et membres interdits dans System.Core.dll](disallowed-types-and-members-in-system-core-dll.md)  
  
  
