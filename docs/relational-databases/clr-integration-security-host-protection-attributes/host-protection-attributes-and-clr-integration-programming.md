---
title: Common Language Runtime (CLR) Attributs de protection de l’hôte
description: Le CLR fournit un mécanisme pour annoter les API gérées dans le cadre .NET avec des attributs tels que SharedState, Synchronization, et ExternalProcessMgmt.
ms.custom: seo-lt-2019
ms.date: 03/17/2017
ms.prod: sql
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
ms.openlocfilehash: 2aeaeb5d4eb06d6d632a59300225d01cc4376369
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488050"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a>Attributs de protection de l'hôte et programmation de l'intégration CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Le Common Language Runtime (CLR) fournit un mécanisme pour annoter des interfaces de programmation d'applications (API) managées qui font partie du .NET Framework avec certains attributs qui peuvent intéresser un hôte du CLR, tel que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], à compter de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Voici quelques exemples d'attributs de protection de l'hôte (HPA, Host Protection Attribute) :  
  
-   **SharedState**, qui indique si l’API expose la capacité de créer ou de gérer l’état partagé (par exemple, les champs de classe statique).  
  
-   **Synchronisation**, qui indique si l’API expose la capacité d’effectuer la synchronisation entre les threads.  
  
-   **ExternalProcessMgmt**, qui indique si l’API expose un moyen de contrôler le processus d’accueil.  
  
 Étant donné ces attributs, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifie une liste de HPA rejetés dans l'environnement hébergé par le biais de la sécurité d'accès du code. Les exigences de la SAE sont spécifiées par l’un des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trois ensembles d’autorisation : **SAFE**, **EXTERNAL_ACCESS**, ou **UNSAFE**. L’un de ces trois niveaux de sécurité est spécifié lorsque l’assemblage est enregistré sur le serveur, en utilisant la déclaration **CREATE ASSEMBLY.** L’exécution du code dans les ensembles **d’autorisation SAFE** ou **EXTERNAL_ACCESS** doit éviter certains types ou membres qui ont **l’attribut System.Security.Permissions.HostProtectionAttribute** appliqué. Pour plus d’informations, voir [Créer une assemblée](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md) et [CLR Integration Programming Model Restrictions](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md).  
  
 **L’HostProtectionAttribute** n’est pas une autorisation de sécurité autant qu’un moyen d’améliorer la fiabilité, en ce sens qu’il identifie des constructions de code spécifiques, types ou méthodes, que l’hôte peut refuser. L’utilisation de **l’HostProtectionAttribute** applique un modèle de programmation qui aide à protéger la stabilité de l’hôte.  
  
## <a name="host-protection-attributes"></a>Attributs de protection de l'hôte  
 Les attributs de protection de l'hôte identifient des types ou des membres qui ne sont pas adaptés au modèle de programmation hôte et représentent les niveaux croissants suivants de menace en termes de fiabilité :  
  
-   Sans gravité par ailleurs.  
  
-   Susceptible de déstabiliser le code utilisateur géré par le serveur.  
  
-   Susceptible de déstabiliser le processus serveur lui-même.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]interdit l’utilisation d’un type ou d’un membre qui a un **HostProtectionAttribute** qui spécifie un **System.Security.Permissions.HostProtectionResource** énumération avec une valeur de **ExternalProcessMgmt**, **ExternalThreading**, **MayLeakOnAbort**, **SecurityInfrastructure**, **SelfAffectingProcessMgmnt**, **SelfAffectingThreading**, **SharedState**, **Synchronization**, ou **UI**. Cela empêche les assemblys d'appeler des membres qui activent l'état de partage, exécutent la synchronisation, peuvent entraîner une fuite de ressources ou affectent l'intégrité du processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="disallowed-types-and-members"></a>Types et membres rejetés  
 Les sujets suivants identifient les types et les membres dont [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]les valeurs **HostProtectionResource** sont refusées par .  
  
> [!NOTE]  
>  Les listes de ces rubriques ont été générées à partir des assemblys pris en charge.  Pour plus d’informations, voir [Supported .NET Framework Libraries](../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Types et membres interdits dans Microsoft.VisualBasic.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-microsoft-visualbasic-dll.md)  
 Répertorie les types et membres dans Microsoft.VisualBasic.dll dont les valeurs HPA sont rejetées.  
  
 [Types et membres interdits dans mscorlib.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-mscorlib-dll.md)  
 Répertorie les types et membres dans mscorlib.dll dont les valeurs HPA sont rejetées.  
  
 [Types et membres non autorisés dans System.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-dll.md)  
 Répertorie les types et membres dans System.dll dont les valeurs HPA sont rejetées.  
  
 [Types et membres non autorisés dans System.Data.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-data-dll.md)  
 Répertorie les types et membres dans System.Data.dll dont les valeurs HPA sont rejetées.  
  
 [Types et membres interdits dans System.Core.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-core-dll.md)  
 Répertorie les types et membres dans System.Core.dll dont les valeurs HPA sont rejetées.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité d’accès au Code d’intégration CLR](../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Restrictions du modèle de programmation d’intégration CLR](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Création d'un assembly](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
