---
title: Restrictions du modèle de programmation de l’intégration du CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: a9b51e0fc192c94b32b4d496523dbf3c9216efd6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62873815"
---
# <a name="clr-integration-programming-model-restrictions"></a>Restrictions du modèle de programmation de l'intégration du CLR
  Lors de la génération d’une procédure stockée managée ou d’un autre objet de base de données managée, certaines vérifications du code effectuées par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] effectuent des vérifications sur l’assembly de code `CREATE ASSEMBLY` managé lorsqu’il est inscrit pour la première fois dans la base de données, à l’aide de l’instruction et également au moment de l’exécution. Le code managé est également vérifié pendant l'exécution, car dans un assembly il peut y avoir des chemins d'accès de code qui peuvent ne jamais être atteints pendant l'exécution.  Cela fournit la souplesse nécessaire pour inscrire notamment des assemblys tiers, afin qu'un assembly ne soit pas bloqué là où il y a du code « potentiellement dangereux » conçu pour s'exécuter dans un environnement client, mais ne soit jamais exécuté dans le CLR hébergé. Les exigences que le code managé doit respecter varient selon que l’assembly est inscrit `SAFE`en `EXTERNAL_ACCESS`tant que `UNSAFE`, `SAFE` ou, et qu’il est le plus strict, et est répertorié ci-dessous.  
  
 En plus des restrictions imposées sur les assemblys de code managé, des autorisations de sécurité du code sont également accordées. Le Common Language Runtime (CLR) prend en charge un modèle de sécurité appelé sécurité d'accès du code pour le code managé. Dans ce modèle, les autorisations sont accordées aux assemblys selon l'identité du code. Les assemblys `SAFE`, `EXTERNAL_ACCESS` et `UNSAFE` ont des autorisations de sécurité d'accès du code différentes. Pour plus d’informations, consultez [sécurité d’accès du code d’intégration du CLR](../security/clr-integration-code-access-security.md).  
  
## <a name="create-assembly-checks"></a>Contrôles CREATE ASSEMBLY  
 Lorsque l'instruction `CREATE ASSEMBLY` est exécutée, les contrôles suivants sont effectués pour chaque niveau de sécurité.  Si un contrôle échoue, `CREATE ASSEMBLY` échoue avec un message d'erreur.  
  
### <a name="global-any-security-level"></a>Global (tout niveau de sécurité)  
 Tous les assemblys référencés doivent satisfaire un ou plusieurs des critères suivants :  
  
-   L'assembly est déjà inscrit dans la base de données.  
  
-   L'assembly est l'un des assemblys pris en charge. Pour plus d’informations, consultez [.NET Framework les bibliothèques prises en charge](supported-net-framework-libraries.md).  
  
-   Vous utilisez l' `CREATE ASSEMBLY FROM` * \<emplacement>,* et tous les assemblys référencés et leurs dépendances sont disponibles dans * \<emplacement>*.  
  
-   Vous utilisez `CREATE ASSEMBLY FROM` * \<bytes... >,* et toutes les références sont spécifiées via des octets séparés par des espaces.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Tous les assemblys `EXTERNAL_ACCESS` doivent répondre aux critères suivants :  
  
-   Les champs statiques ne sont pas utilisés pour stocker des informations. Les champs statiques en lecture seule sont autorisés.  
  
-   Le test PEVerify est réussi. L'outil PEVerify (peverify.exe), qui vérifie que le code MSIL et les métadonnées associées satisfont les spécifications de sécurité de type, est fourni dans le Kit de développement SDK .NET Framework.  
  
-   La synchronisation, par exemple avec la classe `SynchronizationAttribute`, n'est pas utilisée.  
  
-   Les méthodes finaliseurs ne sont pas utilisées.  
  
 Les attributs personnalisés suivants sont interdits dans les assemblys `EXTERNAL_ACCESS` :  
  
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
  
-   Toutes les conditions d'assembly `EXTERNAL_ACCESS` sont vérifiées.  
  
## <a name="runtime-checks"></a>Contrôles d'exécution  
 Pendant l'exécution, les conditions suivantes sont vérifiées pour l'assembly de code. Si l'une de ces conditions est remplie, le code managé n'est pas autorisé à s'exécuter et une exception est levée.  
  
### <a name="unsafe"></a>UNSAFE  
 Le chargement d’un assembly, qu’il `System.Reflection.Assembly.Load()` soit explicitement en appelant la méthode à partir d’un tableau d’octets `Reflection.Emit` , ou implicitement par le biais de l’utilisation de l’espace de noms, n’est pas autorisé.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Toutes les conditions `UNSAFE` sont vérifiées.  
  
 Tous les types et méthodes annotés avec les valeurs d'attribut de protection de l'hôte suivantes dans la liste d'assemblys prise en charge sont interdits.  
  
-   SelfAffectingProcessMgmt  
  
-   SelfAffectingThreading  
  
-   Synchronization  
  
-   SharedState  
  
-   ExternalProcessMgmt  
  
-   ExternalThreading  
  
-   SecurityInfrastructure  
  
-   MayLeakOnAbort  
  
-   Interface utilisateur  
  
 Pour plus d’informations sur hPa et pour obtenir la liste des types et des membres non autorisés dans les assemblys pris en charge, consultez attributs de protection de l' [hôte et programmation](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)de l’intégration du CLR.  
  
### <a name="safe"></a>SAFE  
 Toutes les conditions `EXTERNAL_ACCESS` sont vérifiées.  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèques de .NET Framework prises en charge](supported-net-framework-libraries.md)   
 [Sécurité d’accès du code d’intégration du CLR](../security/clr-integration-code-access-security.md)   
 [Attributs de protection de l’hôte et programmation de l’intégration du CLR](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Création d'un assembly](../assemblies/creating-an-assembly.md)  
  
  
