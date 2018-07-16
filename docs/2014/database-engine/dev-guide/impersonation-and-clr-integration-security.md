---
title: L’emprunt d’identité et de sécurité de l’intégration CLR | Microsoft Docs
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
- impersonation [CLR integration]
- security [CLR integration]
- execution context [CLR integration]
- user impersonation [CLR integration]
- context [CLR integration]
ms.assetid: 1495a7af-2248-4cee-afdb-9269fb3a7774
caps.latest.revision: 17
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 05b117f27d0c27ca9288f94aade079df876fafad
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37243199"
---
# <a name="impersonation-and-clr-integration-security"></a>Emprunt d'identité et sécurité de l'intégration du CLR
  Lorsque du code managé accède à des ressources externes, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'emprunte pas automatiquement l'identité du contexte d'exécution actuel sous lequel la routine s'exécute. Le code dans les assemblys `EXTERNAL_ACCESS` et `UNSAFE` peut emprunter l'identité du contexte d'exécution actuel de manière explicite.  
  
> [!NOTE]  
>  Pour plus d’informations sur les changements de comportement d’emprunt d’identité, consultez [modifications avec rupture des fonctionnalités du moteur de base de données dans SQL Server 2014](../breaking-changes-to-database-engine-features-in-sql-server-2016.md).  
  
 Le fournisseur d'accès aux données in-process fournit une interface de programmation d'applications, `SqlContext.WindowsIdentity`, qui peut être utilisée pour extraire le jeton associé au contexte de sécurité actuel. Le code managé dans les assemblys `EXTERNAL_ACCESS` et `UNSAFE` peut utiliser cette méthode pour extraire le contexte et utiliser la méthode `WindowsIdentity.Impersonate` .NET Framework pour emprunter l'identité de contexte. Les restrictions suivantes s'appliquent lorsque le code utilisateur emprunte l'identité de manière explicite :  
  
-   L'accès aux données in-process n'est pas autorisé lorsque le code managé est dans un état d'emprunt d'identité. Le code peut annuler l'emprunt d'identité, puis appeler l'accès aux données in-process. Notez que cela requiert le stockage de la valeur de retour (un objet `WindowsImpersonationContext`) de la méthode `Impersonate` d'origine, puis l'appel à la méthode `Undo` sur ce `WindowsImpersonationContext`.  
  
     Cette restriction signifie que lorsque l'accès aux données in-process se produit, c'est toujours dans le contexte de sécurité actuel effectif pour la session. Cela ne peut pas être modifié par l'emprunt d'identité explicite dans le code managé.  
  
-   Pour le code managé qui s'exécute de façon asynchrone (par exemple, par le biais d'assemblys `UNSAFE` créant des threads et exécutant du code de façon asynchrone), l'accès aux données in-process n'est jamais autorisé. Cela est vrai qu'il y ait emprunt d'identité ou non.  
  
 Lorsque le code s'exécute dans un contexte dont l'identité a été empruntée qui est différent de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il ne peut pas effectuer d'appels d'accès aux données in-process ; il doit annuler le contexte d'emprunt d'identité avant d'effectuer des appels d'accès aux données in-process. Lorsque l'accès aux données in-process est effectué à partir de code managé, le contexte d'exécution d'origine du point d'entrée [!INCLUDE[tsql](../../includes/tsql-md.md)] dans le code managé est toujours utilisé pour l'autorisation.  
  
 Les assemblys `EXTERNAL_ACCESS` et `UNSAFE` accèdent tous deux aux ressources de système d'exploitation avec le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], à moins qu'ils n'empruntent volontairement l'identité du contexte de sécurité actuel comme décrit précédemment. Pour cette raison, les auteurs des assemblys `EXTERNAL_ACCESS` nécessitent un niveau supérieur d'approbation que ceux des assemblys `SAFE`, spécifié par l'autorisation au niveau de la connexion `EXTERNAL ACCESS`. L'autorisation `EXTERNAL ACCESS` doit être accordée uniquement aux connexions approuvées pour exécuter du code sous le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité d’intégration du CLR](../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [Emprunt d’identité et informations d’identification pour les connexions](../../relational-databases/clr-integration/data-access/impersonation-and-credentials-for-connections.md)  
  
  
