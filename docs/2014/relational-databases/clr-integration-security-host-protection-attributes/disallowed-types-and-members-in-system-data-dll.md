---
title: Interdit les Types et membres dans System.Data.dll | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: ee5f55e9-fbef-401a-be18-a2e5873c8720
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7c222c10fe13a422e5195970057fbb623cc960a4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043872"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a>Types et membres dans System.Data.dll interdits
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] programmation de l’intégration (CLR) langage commun n’autorise pas l’utilisation d’un type ou un membre qui a un `HostProtectionAttribute` qui spécifie un `System.Security.Permissions.HostProtectionResource` énumération avec la valeur `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, **SharedState**, `Synchronization`, ou `UI`. Le tableau suivant répertorie les membres et les types de l'assembly System.Data dll dont les valeurs d'attribut de protection de l'hôte (HPA) sont interdites.  
  
> [!NOTE]  
>  Cette liste a été générée à partir des assemblys pris en charge. Pour plus d’informations, consultez [prise en charge des bibliothèques .NET Framework](../clr-integration/database-objects/supported-net-framework-libraries.md).  
  
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
 [Attributs de Protection d’hôte et de la programmation de l’intégration CLR](host-protection-attributes-and-clr-integration-programming.md)   
 [Types et membres dans Microsoft.VisualBasic.dll interdits](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [Types et membres dans mscorlib.dll interdits](disallowed-types-and-members-in-mscorlib-dll.md)   
 [Types et membres dans System.dll interdits](disallowed-types-and-members-in-system-dll.md)   
 [Types et membres non autorisés dans System.Core.dll](disallowed-types-and-members-in-system-core-dll.md)  
  
  