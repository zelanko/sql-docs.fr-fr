---
title: Restrictions du modèle de programmation d’intégration CLR (fr) Microsoft Docs
description: SQL Server effectue des vérifications de code sur les objets de base de données gérés lorsqu’ils sont enregistrés pour la première fois à l’aide de CREATE ASSEMBLY et à l’heure d’exécution.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
author: rothja
ms.author: jroth
ms.openlocfilehash: 83b73909cf1844796640a83910ee609eadd7dba4
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488528"
---
# <a name="clr-integration-programming-model-restrictions"></a>Restrictions du modèle de programmation de l'intégration du CLR
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Lorsque vous construisez une procédure stockée gérée ou un autre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] objet de base de données géré, il y a certaines vérifications de code effectuées par qui doivent être prises en considération. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]effectue des vérifications sur l’assemblage de code géré lorsqu’il est enregistré pour la première fois dans la base de données, à l’aide de l’instruction **CREATE ASSEMBLY,** ainsi qu’au moment de l’exécution. Le code managé est également vérifié pendant l'exécution, car dans un assembly il peut y avoir des chemins d'accès de code qui peuvent ne jamais être atteints pendant l'exécution.  Cela fournit la souplesse nécessaire pour inscrire notamment des assemblys tiers, afin qu'un assembly ne soit pas bloqué là où il y a du code « potentiellement dangereux » conçu pour s'exécuter dans un environnement client, mais ne soit jamais exécuté dans le CLR hébergé. Les exigences que le code géré doit satisfaire dépendent de la question de savoir si l’assemblage est enregistré comme **SAFE**, **EXTERNAL_ACCESS**, ou **UNSAFE**, **SAFE** étant le plus strict, et sont énumérés ci-dessous.  
  
 En plus des restrictions imposées sur les assemblys de code managé, des autorisations de sécurité du code sont également accordées. Le Common Language Runtime (CLR) prend en charge un modèle de sécurité appelé sécurité d'accès du code pour le code managé. Dans ce modèle, les autorisations sont accordées aux assemblys selon l'identité du code. **SAFE**, **EXTERNAL_ACCESS**, et les assemblages **UNSAFE** ont différentes autorisations de CAS. Pour plus d’informations, voir [CLR Integration Code Access Security](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md).  
  
## <a name="create-assembly-checks"></a>Contrôles CREATE ASSEMBLY  
 Lorsque l’instruction **CREATE ASSEMBLY** est exécutée, les contrôles suivants sont effectués pour chaque niveau de sécurité.  En cas d’échec de la vérification, **CREATE ASSEMBLY** échouera avec un message d’erreur.  
  
### <a name="global-any-security-level"></a>Global (tout niveau de sécurité)  
 Tous les assemblys référencés doivent satisfaire un ou plusieurs des critères suivants :  
  
-   L'assembly est déjà inscrit dans la base de données.  
  
-   L'assembly est l'un des assemblys pris en charge. Pour plus d’informations, voir [Supported .NET Framework Libraries](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
-   Vous utilisez **CREATE ASSEMBLY DE**_\<l’emplacement>,_ et tous les assemblages référencés et leurs dépendances sont disponibles dans * \<l’emplacement>*.  
  
-   Vous utilisez **CREATE ASSEMBLY FROM**_\<octets ... >,_ et toutes les références sont spécifiées via l’espace séparés octets.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Toutes les **EXTERNAL_ACCESS** assemblées doivent répondre aux critères suivants :  
  
-   Les champs statiques ne sont pas utilisés pour stocker des informations. Les champs statiques en lecture seule sont autorisés.  
  
-   Le test PEVerify est réussi. L'outil PEVerify (peverify.exe), qui vérifie que le code MSIL et les métadonnées associées satisfont les spécifications de sécurité de type, est fourni dans le Kit de développement SDK .NET Framework.  
  
-   La synchronisation, par exemple avec la classe **SynchronizationAttribute,** n’est pas utilisée.  
  
-   Les méthodes finaliseurs ne sont pas utilisées.  
  
 Les attributs personnalisés suivants sont refusés dans **EXTERNAL_ACCESS** assemblées :  
  
-   System.ContextStaticAttribute  
  
-   System.MTAThreadAttribute  
  
-   System.Runtime.CompilerServices.MethodImplAttribute  
  
-   System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
  
-   System.Runtime.Remoting.Contexts.ContextAttribute  
  
-   System.Runtime.Remoting.Contexts.SynchronizationAttribute  
  
-   System.Runtime.InteropServices.DllImportAttribute  
  
-   System.Security.Permissions.CodeAccessSecurityAttribute  
  
-   System.Security.SuppressUnmanagedCodeSecurityAttribute  
  
-   System.Security.UnverifiableCodeAttribute  
  
-   System.STAThreadAttribute  
  
-   System.ThreadStaticAttribute  
  
### <a name="safe"></a>SAFE  
  
-   Toutes les **conditions d’assemblage EXTERNAL_ACCESS** sont vérifiées.  
  
## <a name="runtime-checks"></a>Contrôles d'exécution  
 Pendant l'exécution, les conditions suivantes sont vérifiées pour l'assembly de code. Si l'une de ces conditions est remplie, le code managé n'est pas autorisé à s'exécuter et une exception est levée.  
  
### <a name="unsafe"></a>UNSAFE  
 Le chargement d’une assemblage - soit explicitement en appelant la méthode **System.Reflection.Assembly.Load()** à partir d’un tableau de byte, ou implicitement par l’utilisation de **Reflection.Emit** namespace- n’est pas autorisé.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Toutes les conditions **DE l’INSU** sont vérifiées.  
  
 Tous les types et méthodes annotés avec les valeurs d'attribut de protection de l'hôte suivantes dans la liste d'assemblys prise en charge sont interdits.  
  
-   SelfAffectingProcessMgmt  
  
-   SelfAffectingThreading  
  
-   Synchronization  
  
-   SharedState  
  
-   ExternalProcessMgmt  
  
-   ExternalThreading  
  
-   SecurityInfrastructure  
  
-   MayLeakOnAbort  
  
-   UI  
  
 Pour plus d’informations sur les ZSM et une liste de types et de membres refusés dans les assemblées assistées, voir [attributs de protection des hôtes et clR Integration Programming](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md).  
  
### <a name="safe"></a>SAFE  
 Toutes les **conditions EXTERNAL_ACCESS** sont vérifiées.  
  
## <a name="see-also"></a>Voir aussi  
 [Supported .NET Framework Libraries](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)   
 [Sécurité d’accès au Code d’intégration CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Attributs de protection des hôtes et programmation d’intégration CLR](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Création d'un assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
