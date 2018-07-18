---
title: Création d’objets de base de données avec l’intégration du Common Language Runtime (CLR) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- database objects [CLR integration], building
- common language runtime [SQL Server], building database objects
- managed code [SQL Server], database objects
- building database objects [CLR integration]
- .NET Framework routines [SQL Server]
ms.assetid: ce34132c-bfa3-447b-9131-b6e17c672efe
caps.latest.revision: 47
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 72d68e213d240e3c6182f99e8c1637c1f1ebedfb
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37351011"
---
# <a name="building-database-objects-with-common-language-runtime-clr-integration"></a>Création d'objets de base de données avec intégration du Common Language Runtime (CLR)
  Vous pouvez créer des objets de base de données à l’aide de la [!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est appelé « routine CLR ». Ces routines incluent :  
  
-   Fonctions scalaires définies par l'utilisateur (fonctions UDF scalaires)  
  
-   Fonctions table définies par l'utilisateur (TVF)  
  
-   Procédures définies par l'utilisateur (UDP)  
  
-   Déclencheurs définis par l’utilisateur  
  
 Les routines CLR ont la même structure en code managé. Elles sont mappées à des méthodes statiques publiques (partagées dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET) d'une classe. Outre les routines, les types définis par l'utilisateur (UDT) et les fonctions d'agrégation définies par l'utilisateur peuvent également être définies à l'aide du .NET Framework. Les types UDT et les agrégats définis par l'utilisateur sont mappés à des classes .NET Framework entières.  
  
 Chaque type de routine du .NET Framework possède un [!INCLUDE[tsql](../../../includes/ssnoversion-md.md)] qui le [!INCLUDE[tsql](../../../includes/tsql-md.md)] équivalent peut être utilisé. Par exemple, les fonctions UDF scalaires peuvent être utilisées dans toute expression scalaire. Une fonction TVF peut être utilisée dans toute clause FROM. Une procédure peut être appelée dans une instruction EXEC ou à partir d'une application cliente.  
  
> [!NOTE]  
>  L'exécution d'un objet CLR (fonction définie par l'utilisateur, type défini par l'utilisateur ou déclencheur) sur le Common Language Runtime peut concerner plusieurs threads (plan parallèle), si l'optimiseur de requêtes décide que cela est nécessaire. Toutefois, si une fonction définie par l'utilisateur accède aux données, l'exécution se fera sur un plan en série. En cas d'exécution sur une version serveur antérieure à [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], si une fonction définie par l'utilisateur contient des paramètres LOB ou des valeurs de retour, l'exécution doit également se faire sur un plan en série.  
  
 Le tableau ci-dessous répertorie les rubriques traitées dans cette section.  
  
 [Prise en main de l’intégration du CLR](getting-started-with-clr-integration.md)  
 Fournit une brève vue d'ensemble des bibliothèques et des espaces de noms requis pour compiler l'objet en utilisant l'intégration du CLR avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Inclut un exemple de procédure stockée CLR "Hello World".  
  
 [Bibliothèques .NET Framework prises en charge](supported-net-framework-libraries.md)  
 Fournit des informations sur les bibliothèques .NET Framework prises en charge par l'intégration du CLR.  
  
 [Restrictions du modèle de programmation de l’intégration du CLR](clr-integration-programming-model-restrictions.md)  
 Fournit des informations sur les restrictions du modèle de programmation de l'intégration du CLR.  
  
 [Types de données SQL Server dans .NET Framework](../../clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
 Vue d'ensemble de types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et de leurs équivalents .NET Framework.  
  
 [Vue d’ensemble des attributs personnalisés de l’intégration du CLR](../../../database-engine/dev-guide/overview-of-clr-integration-custom-attributes.md)  
 Fournit des informations sur les attributs personnalisés de l'intégration du CLR.  
  
 [Fonctions CLR définies par l’utilisateur](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)  
 Explique comment implémenter et utiliser les différents types de fonctions CLR : fonctions table, scalaires et d'agrégation définies par l'utilisateur.  
  
 [Types CLR définis par l’utilisateur](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
 Explique comment implémenter et utiliser les types CLR définis par l'utilisateur.  
  
 [Procédures stockées du CLR](../../../database-engine/dev-guide/clr-stored-procedures.md)  
 Explique comment implémenter et utiliser les procédures stockées CLR.  
  
 [Déclencheurs CLR](../../../database-engine/dev-guide/clr-triggers.md)  
 Explique comment implémenter et utiliser les déclencheurs CLR.  
  
## <a name="see-also"></a>Voir aussi  
 [Common Language Runtime &#40;CLR&#41; présentation de l’intégration](../common-language-runtime-integration-overview.md)  
  
  
