---
title: Attributs de protection de l’hôte du Common Language Runtime (CLR)
description: Le common language runtime (CLR) fournit un mécanisme pour annoter les interfaces de programmation d’applications (API) managées qui font partie du .NET Framework avec certains attributs.
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
ms.openlocfilehash: 733e4adc69570dd98e6e0ad5448820607ade6329
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75258756"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a>Attributs de protection de l'hôte et programmation de l'intégration CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Le Common Language Runtime (CLR) fournit un mécanisme pour annoter des interfaces de programmation d'applications (API) managées qui font partie du .NET Framework avec certains attributs qui peuvent intéresser un hôte du CLR, tel que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], à compter de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Voici quelques exemples d'attributs de protection de l'hôte (HPA, Host Protection Attribute) :  
  
-   **SharedState**, qui indique si l’API expose la capacité à créer ou gérer l’état partagé (par exemple, les champs de classe statique).  
  
-   La **synchronisation**, qui indique si l’API expose la possibilité d’effectuer une synchronisation entre les threads.  
  
-   **ExternalProcessMgmt**, qui indique si l’API expose un moyen de contrôler le processus hôte.  
  
 Étant donné ces attributs, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifie une liste de HPA rejetés dans l'environnement hébergé par le biais de la sécurité d'accès du code. Les conditions requises pour les autorités de certification sont [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifiées par l’un des trois jeux d’autorisations : **Safe**, **EXTERNAL_ACCESS**ou **unsafe**. L’un de ces trois niveaux de sécurité est spécifié lorsque l’assembly est inscrit sur le serveur, à l’aide de l’instruction **Create Assembly** . Le code qui s’exécute dans les jeux d’autorisations **Safe** ou **EXTERNAL_ACCESS** doit éviter certains types ou membres dont l’attribut **System. Security. Permissions. HostProtectionAttribute** est appliqué. Pour plus d’informations, consultez [création d’un assembly](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md) et [restrictions du modèle de programmation](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)de l’intégration du CLR.  
  
 Le **HostProtectionAttribute** n’est pas une autorisation de sécurité autant qu’un moyen d’améliorer la fiabilité, en ce sens qu’il identifie des constructions de code spécifiques, que ce soit des types ou des méthodes, que l’hôte peut rejeter. L’utilisation de **HostProtectionAttribute** applique un modèle de programmation qui permet de protéger la stabilité de l’hôte.  
  
## <a name="host-protection-attributes"></a>Attributs de protection de l'hôte  
 Les attributs de protection de l'hôte identifient des types ou des membres qui ne sont pas adaptés au modèle de programmation hôte et représentent les niveaux croissants suivants de menace en termes de fiabilité :  
  
-   Sans gravité par ailleurs.  
  
-   Susceptible de déstabiliser le code utilisateur géré par le serveur.  
  
-   Susceptible de déstabiliser le processus serveur lui-même.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]interdit l’utilisation d’un type ou d’un membre ayant un **HostProtectionAttribute** qui spécifie une énumération **System. Security. Permissions. HostProtectionResource** avec la valeur **ExternalProcessMgmt**, **ExternalThreading**, **MayLeakOnAbort**, **SecurityInfrastructure**, **SelfAffectingProcessMgmnt**, **SelfAffectingThreading**, **SharedState**, la **synchronisation**ou **l’interface utilisateur**. Cela empêche les assemblys d'appeler des membres qui activent l'état de partage, exécutent la synchronisation, peuvent entraîner une fuite de ressources ou affectent l'intégrité du processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="disallowed-types-and-members"></a>Types et membres rejetés  
 Les rubriques suivantes identifient les types et les membres dont les valeurs **HostProtectionResource** ne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sont pas autorisées par.  
  
> [!NOTE]  
>  Les listes de ces rubriques ont été générées à partir des assemblys pris en charge.  Pour plus d’informations, consultez [.NET Framework les bibliothèques prises en charge](../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
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
 [Sécurité d’accès du code d’intégration du CLR](../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Restrictions du modèle de programmation de l’intégration du CLR](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Création d’un assembly](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
