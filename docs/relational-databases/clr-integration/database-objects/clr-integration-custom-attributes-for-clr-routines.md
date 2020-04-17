---
title: Attributs personnalisés pour les routines CLR Microsoft Docs
description: Les attributs personnalisés peuvent être appliqués aux routines CLR, aux types définis par l’utilisateur et aux agrégats définis par l’utilisateur qui sont enregistrés dans Microsoft SQL Server.
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
ms.openlocfilehash: a32a606f73858ede15569d1ade891ad2ce1c69a5
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487949"
---
# <a name="clr-integration-custom-attributes-for-clr-routines"></a>Attributs personnalisés de l’intégration du CLR pour les routines CLR
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Les attributs énumérés peuvent être appliqués aux routines courantes d’exécution de langue (CLR), [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]aux types définis par l’utilisateur et aux agrégats définis par l’utilisateur qui sont enregistrés dans . Si l'attribut n'est pas appliqué, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise la valeur par défaut. Les attributs énumérés sont définis dans le namespace **Microsoft.SqlServer.Server.**  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a>Attribut SqlUserDefinedAggregate  
 **L’attribut SqlUserDefinedAggregate** indique que la méthode doit être enregistrée comme un agrégat défini par l’utilisateur. Chaque agrégat défini par l'utilisateur doit être annoté avec cet attribut.  
  
 Pour plus d’informations, voir [SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626).  
  
## <a name="the-sqlfunction-attribute"></a>Attribut SqlFunction  
 **L’attribut SqlFunction** indique que la méthode doit être enregistrée en fonction, avec l’ensemble approprié d’attributs de fonction.  
  
 Pour plus d’informations, voir [SqlFunctionAttribute](https://go.microsoft.com/fwlink/?LinkId=128019).  
  
## <a name="the-sqlfacet-attribute"></a>Attribut SqlFacet  
 **L’attribut SqlFacet** est utilisé pour retourner des informations sur le type de retour d’une expression de type utilisateur définie (UDT).  
  
 Pour plus d’informations, voir [SqlFacetAttribute](https://go.microsoft.com/fwlink/?LinkId=128020).  
  
## <a name="the-sqlprocedure-attribute"></a>Attribut SqlProcedure  
 **L’attribut SqlProcedure** indique que la méthode doit être enregistrée comme une procédure stockée. Cet attribut est utilisé uniquement par Visual Studio pour inscrire automatiquement la méthode spécifiée en tant que procédure stockée ; il n'est pas utilisé par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Pour plus d’informations, voir [SqlProcedureAttribute](https://go.microsoft.com/fwlink/?LinkId=128021).  
  
## <a name="the-sqltrigger-attribute"></a>Attribut SqlTrigger  
 **L’attribut SqlTrigger** indique que la méthode doit être enregistrée comme déclencheur.  
  
 Pour plus d’informations, voir [SqlTriggerContext](https://go.microsoft.com/fwlink/?LinkId=128022) et [SqlTriggerAttribute](https://go.microsoft.com/fwlink/?LinkId=203898).  
  
## <a name="the-sqluserdefinedtypeattribute"></a>SqlUserDefinedTypeAttribute  
 Vous pouvez appliquer SqlUserDefinedTypeAttribute à une définition de classe dans l'assembly. Cela oblige [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à créer un type défini par l'utilisateur et lié à la définition de classe qui possède cet attribut personnalisé.  
  
 Pour plus d’informations, voir [SqlUserDefinedTypeAttribute](https://go.microsoft.com/fwlink/?LinkId=128024).  
  
## <a name="the-sqlmethod-attribute"></a>Attribut SqlMethod  
 **L’attribut SqlMethod** est utilisé pour indiquer le déterminisme et les propriétés d’accès aux données d’une méthode ou d’une propriété sur un UDT.  
  
 Pour plus d’informations, voir [SqlMethodAttribute](https://go.microsoft.com/fwlink/?LinkId=128025).  
  
## <a name="see-also"></a>Voir aussi  
 [Agrégats définis par l’utilisateur CLR](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)   
 [Fonctions définies par l’utilisateur CLR](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [Types définis par l’utilisateur CLR](../../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [Procédures stockées CLR](https://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)   
 [Déclencheurs CLR](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)  
  
  
