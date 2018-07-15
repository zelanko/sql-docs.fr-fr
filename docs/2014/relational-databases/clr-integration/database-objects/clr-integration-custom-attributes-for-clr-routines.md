---
title: Les attributs personnalisés pour les Routines CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
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
caps.latest.revision: 82
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a2f3e1980c164327e584d8f485c2d08571534245
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37351041"
---
# <a name="custom-attributes-for-clr-routines"></a>Attributs personnalisés pour les routines CLR
  Les attributs répertoriés peuvent être appliqués au common language runtime (CLR) routines, types définis par l’utilisateur et les agrégats définis par l’utilisateur qui sont inscrits dans [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)]. Si l'attribut n'est pas appliqué, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise la valeur par défaut. Les attributs répertoriés sont définis dans l'espace de noms `Microsoft.SqlServer.Server`.  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a>Attribut SqlUserDefinedAggregate  
 L'attribut `SqlUserDefinedAggregate` indique que la méthode doit être inscrite en tant qu'agrégat défini par l'utilisateur. Chaque agrégat défini par l'utilisateur doit être annoté avec cet attribut.  
  
 Pour plus d’informations, consultez [SqlUserDefinedAggregateAttribute](http://go.microsoft.com/fwlink/?LinkId=124626).  
  
## <a name="the-sqlfunction-attribute"></a>Attribut SqlFunction  
 L'attribut `SqlFunction` indique que la méthode doit être inscrite en tant que fonction, avec les attributs de fonctions appropriés définis.  
  
 Pour plus d’informations, consultez [SqlFunctionAttribute](http://go.microsoft.com/fwlink/?LinkId=128019).  
  
## <a name="the-sqlfacet-attribute"></a>Attribut SqlFacet  
 L'attribut `SqlFacet` est utilisé pour retourner des informations sur le type de retour d'une expression de type défini par l'utilisateur.  
  
 Pour plus d’informations, consultez [SqlFacetAttribute](http://go.microsoft.com/fwlink/?LinkId=128020).  
  
## <a name="the-sqlprocedure-attribute"></a>Attribut SqlProcedure  
 L'attribut `SqlProcedure` indique que la méthode doit être inscrite en tant que procédure stockée. Cet attribut est utilisé uniquement par Visual Studio pour inscrire automatiquement la méthode spécifiée en tant que procédure stockée ; il n'est pas utilisé par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Pour plus d’informations, consultez [SqlProcedureAttribute](http://go.microsoft.com/fwlink/?LinkId=128021).  
  
## <a name="the-sqltrigger-attribute"></a>Attribut SqlTrigger  
 L'attribut `SqlTrigger` indique que la méthode doit être inscrite en tant que déclencheur.  
  
 Pour plus d’informations, consultez [SqlTriggerContext](http://go.microsoft.com/fwlink/?LinkId=128022) et [SqlTriggerAttribute](http://go.microsoft.com/fwlink/?LinkId=203898).  
  
## <a name="the-sqluserdefinedtypeattribute"></a>SqlUserDefinedTypeAttribute  
 Vous pouvez appliquer SqlUserDefinedTypeAttribute à une définition de classe dans l'assembly. Cela oblige [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à créer un type défini par l'utilisateur et lié à la définition de classe qui possède cet attribut personnalisé.  
  
 Pour plus d’informations, consultez [SqlUserDefinedTypeAttribute](http://go.microsoft.com/fwlink/?LinkId=128024).  
  
## <a name="the-sqlmethod-attribute"></a>Attribut SqlMethod  
 L'attribut `SqlMethod` est utilisé pour indiquer les propriétés de déterminisme et d'accès aux données d'une méthode ou d'une propriété sur un type défini par l'utilisateur.  
  
 Pour plus d’informations, consultez [SqlMethodAttribute](http://go.microsoft.com/fwlink/?LinkId=128025).  
  
## <a name="see-also"></a>Voir aussi  
 [Agrégats CLR définis par l’utilisateur](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)   
 [Fonctions CLR définies par l’utilisateur](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [Types CLR définis par l’utilisateur](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [Procédures stockées CLR](../../../database-engine/dev-guide/clr-stored-procedures.md)   
 [Déclencheurs CLR](../../../database-engine/dev-guide/clr-triggers.md)  
  
  
