---
title: Héberger des attributs de Protection et de la programmation de l’intégration CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- HostProtectionAttribute [CLR integration]
- common language runtime [SQL Server], host protection attributes
- disallowed types and members [CLR integration]
- common language runtime [SQL Server], disallowed types and members
- HPAs [CLR integration]
ms.assetid: 268078df-63ca-4c03-a8e7-7108bcea9697
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 68f1f114002ab0ef38c7565a523723a06958048d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62874343"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a>Attributs de protection de l'hôte et programmation de l'intégration CLR
  Le Common Language Runtime (CLR) fournit un mécanisme pour annoter des interfaces de programmation d'applications (API) managées qui font partie du .NET Framework avec certains attributs qui peuvent intéresser un hôte du CLR, tel que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], à compter de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Voici quelques exemples d'attributs de protection de l'hôte (HPA, Host Protection Attribute) :  
  
-   `SharedState`, qui indique si l'API expose la capacité à créer ou gérer l'état partagé (par exemple, champs de classe statique).  
  
-   `Synchronization`, qui indique si l'API expose la capacité à effectuer la synchronisation entre des threads.  
  
-   `ExternalProcessMgmt`, qui indique si l'API expose une méthode pour contrôler le processus hôte.  
  
 Étant donné ces attributs, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifie une liste de HPA rejetés dans l'environnement hébergé par le biais de la sécurité d'accès du code. Les spécifications de sécurité d'accès du code sont indiquées par l'un des trois jeux d'autorisations [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : `SAFE`, `EXTERNAL_ACCESS` ou `UNSAFE`. L'un de ces trois niveaux de sécurité est spécifié lorsque l'assembly est inscrit sur le serveur, à l'aide de l'instruction `CREATE ASSEMBLY`. Le code exécuté dans les jeux d'autorisations `SAFE` ou `EXTERNAL_ACCESS` doit éviter certains types ou membres dont l'attribut `System.Security.Permissions.HostProtectionAttribute` est appliqué. Pour plus d’informations, consultez [création d’un Assembly](../clr-integration/assemblies/creating-an-assembly.md) et [Restrictions du modèle de programmation CLR Integration](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md).  
  
 `HostProtectionAttribute` n'est pas tant une autorisation de sécurité qu'une façon d'améliorer la fiabilité, dans le sens où il identifie des constructions de code spécifiques, à savoir des types ou des méthodes, que l'hôte peut rejeter. L'utilisation de `HostProtectionAttribute` applique un modèle de programmation qui contribue à protéger la stabilité de l'hôte.  
  
## <a name="host-protection-attributes"></a>Attributs de protection de l'hôte  
 Les attributs de protection de l'hôte identifient des types ou des membres qui ne sont pas adaptés au modèle de programmation hôte et représentent les niveaux croissants suivants de menace en termes de fiabilité :  
  
-   Sans gravité par ailleurs.  
  
-   Susceptible de déstabiliser le code utilisateur géré par le serveur.  
  
-   Susceptible de déstabiliser le processus serveur lui-même.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’autorise pas l’utilisation d’un type ou membre qui a un `HostProtectionAttribute` qui spécifie un `System.Security.Permissions.HostProtectionResource` énumération avec la valeur `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, `SharedState`, `Synchronization`, ou `UI`. Cela empêche les assemblys d'appeler des membres qui activent l'état de partage, exécutent la synchronisation, peuvent entraîner une fuite de ressources ou affectent l'intégrité du processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="disallowed-types-and-members"></a>Types et membres rejetés  
 Les rubriques suivantes identifient les types et membres dont les valeurs `HostProtectionResource` sont rejetées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Les listes de ces rubriques ont été générées à partir des assemblys pris en charge.  Pour plus d’informations, consultez [prise en charge des bibliothèques .NET Framework](../clr-integration/database-objects/supported-net-framework-libraries.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Types et membres non autorisés dans Microsoft.VisualBasic.dll](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)  
 Répertorie les types et membres dans Microsoft.VisualBasic.dll dont les valeurs HPA sont rejetées.  
  
 [Types et membres non autorisés dans mscorlib.dll](disallowed-types-and-members-in-mscorlib-dll.md)  
 Répertorie les types et membres dans mscorlib.dll dont les valeurs HPA sont rejetées.  
  
 [Types et membres non autorisés dans System.dll](disallowed-types-and-members-in-system-dll.md)  
 Répertorie les types et membres dans System.dll dont les valeurs HPA sont rejetées.  
  
 [Types et membres non autorisés dans System.Data.dll](disallowed-types-and-members-in-system-data-dll.md)  
 Répertorie les types et membres dans System.Data.dll dont les valeurs HPA sont rejetées.  
  
 [Types et membres non autorisés dans System.Core.dll](disallowed-types-and-members-in-system-core-dll.md)  
 Répertorie les types et membres dans System.Core.dll dont les valeurs HPA sont rejetées.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité d’accès du Code CLR Integration](../clr-integration/security/clr-integration-code-access-security.md)   
 [Restrictions de modèle de programmation de l’intégration de CLR](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Création d’un assembly](../clr-integration/assemblies/creating-an-assembly.md)  
  
  
