---
title: Attributs personnalisés pour les routines CLR | Microsoft Docs
description: Les attributs personnalisés peuvent être appliqués aux routines CLR, aux types définis par l’utilisateur et aux agrégats définis par l’utilisateur qui sont inscrits dans Microsoft SQL Server.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- SqlFacet attribute
- SqlTrigger attribute
- SqlProcedure attribute
- custom attributes [CLR integration]
- SqlUserDefinedAggregate attribute
- attributes [CLR integration]
- SqlMethod attribute
- SqlFunction attribute
- common language runtime [SQL Server], attributes
- SqlUserDefinedTypeAttribute attribute
ms.assetid: 95069d22-b05d-4670-b053-15ee2a664e33
author: rothja
ms.author: jroth
ms.openlocfilehash: bad209c4ddb516167b8048ae73680bc9ea59cc05
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91810804"
---
# <a name="clr-integration-custom-attributes-for-clr-routines"></a>Attributs personnalisés de l’intégration du CLR pour les routines CLR
[!INCLUDE[sql-asdbmi](../../../includes/applies-to-version/sql-asdbmi.md)]
  Les attributs répertoriés peuvent être appliqués à des routines de common language runtime (CLR), des types définis par l’utilisateur et des agrégats définis par l’utilisateur qui sont inscrits dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Si l'attribut n'est pas appliqué, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise la valeur par défaut. Les attributs répertoriés sont définis dans l’espace de noms **Microsoft. SqlServer. Server** .  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a>Attribut SqlUserDefinedAggregate  
 L’attribut **SqlUserDefinedAggregate** indique que la méthode doit être inscrite en tant qu’agrégat défini par l’utilisateur. Chaque agrégat défini par l'utilisateur doit être annoté avec cet attribut.  
  
 Pour plus d’informations, consultez [SqlUserDefinedAggregateAttribute](/dotnet/api/microsoft.sqlserver.server.sqluserdefinedaggregateattribute).  
  
## <a name="the-sqlfunction-attribute"></a>Attribut SqlFunction  
 L’attribut **SqlFunction** indique que la méthode doit être inscrite en tant que fonction, avec les attributs de fonction appropriés définis.  
  
 Pour plus d’informations, consultez [SqlFunctionAttribute](/dotnet/api/microsoft.sqlserver.server.sqlfunctionattribute).  
  
## <a name="the-sqlfacet-attribute"></a>Attribut SqlFacet  
 L’attribut **SqlFacet** est utilisé pour retourner des informations sur le type de retour d’une expression de type défini par l’utilisateur (UDT).  
  
 Pour plus d’informations, consultez [SqlFacetAttribute](/dotnet/api/microsoft.sqlserver.server.sqlfacetattribute).  
  
## <a name="the-sqlprocedure-attribute"></a>Attribut SqlProcedure  
 L’attribut **SqlProcedure** indique que la méthode doit être inscrite en tant que procédure stockée. Cet attribut est utilisé uniquement par Visual Studio pour inscrire automatiquement la méthode spécifiée en tant que procédure stockée ; il n'est pas utilisé par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Pour plus d’informations, consultez [SqlProcedureAttribute](/dotnet/api/microsoft.sqlserver.server.sqlprocedureattribute).  
  
## <a name="the-sqltrigger-attribute"></a>Attribut SqlTrigger  
 L’attribut **SqlTrigger** indique que la méthode doit être inscrite en tant que déclencheur.  
  
 Pour plus d’informations, consultez [SqlTriggerContext](/dotnet/api/microsoft.sqlserver.server.sqltriggercontext) et [il manque SqlTriggerAttribute](/dotnet/api/microsoft.sqlserver.server.sqltriggerattribute).  
  
## <a name="the-sqluserdefinedtypeattribute"></a>SqlUserDefinedTypeAttribute  
 Vous pouvez appliquer SqlUserDefinedTypeAttribute à une définition de classe dans l'assembly. Cela oblige [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à créer un type défini par l'utilisateur et lié à la définition de classe qui possède cet attribut personnalisé.  
  
 Pour plus d’informations, consultez [SqlUserDefinedTypeAttribute](/dotnet/api/microsoft.sqlserver.server.sqluserdefinedtypeattribute).  
  
## <a name="the-sqlmethod-attribute"></a>Attribut SqlMethod  
 L’attribut **SqlMethod** est utilisé pour indiquer le déterminisme et les propriétés d’accès aux données d’une méthode ou d’une propriété sur un type défini par l’utilisateur.  
  
 Pour plus d’informations, consultez [SqlMethodAttribute](/dotnet/api/microsoft.sqlserver.server.sqlmethodattribute).  
  
## <a name="see-also"></a>Voir aussi  
 [Agrégats CLR définis par l’utilisateur](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)   
 [Fonctions CLR définies par l’utilisateur](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [Types CLR définis par l’utilisateur](../../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [Procédures stockées CLR](/dotnet/framework/data/adonet/sql/clr-stored-procedures)   
 [Déclencheurs CLR](/dotnet/framework/data/adonet/sql/clr-triggers)  
  
