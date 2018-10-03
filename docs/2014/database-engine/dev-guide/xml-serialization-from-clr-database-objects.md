---
title: Sérialisation XML à partir d’objets de base de données CLR | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- serialization
- XML serialization [CLR integration]
- common language runtime [SQL Server], XML serialization
- XmlSerializer class
ms.assetid: ac84339b-9384-4710-bebc-01607864a344
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b8125f5b8693eccfc619dd2ee3aed6f203e17dad
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48183169"
---
# <a name="xml-serialization-from-clr-database-objects"></a>Sérialisation XML à partir d'objets de base de données CLR
  La sérialisation XML est nécessaire dans deux scénarios :  
  
-   Appel de services Web à partir d'objets CLR (Common Language Runtime).  
  
-   Conversion d'un type défini par l'utilisateur (UDT) en XML.  
  
 La sérialisation XML réalisée par appel de la classe `XmlSerializer` génère normalement un assembly de sérialisation supplémentaire qui est surchargé dans le projet avec l'assembly source. Toutefois, pour des raisons de sécurité, cette surcharge est désactivée dans le CLR. Par conséquent, pour appeler un service web ou effectuer une conversion à partir de l’UDT en XML à l’intérieur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l’assembly doit être créé manuellement à l’aide d’un outil appelé **Sgen.exe** fourni avec le .NET Framework qui génère la nécessaire assemblys de sérialisation. Lors de l'appel de `XmlSerializer`, l'assembly de sérialisation doit être créé manuellement en procédant comme suit :  
  
1.  Exécutez le **Sgen.exe** outil qui est fourni avec le SDK .NET Framework pour créer l’assembly qui contient les sérialiseurs XML de l’assembly source.  
  
2.  Inscrivez l'assembly généré dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de l'instruction `CREATE ASSEMBLY`.  
  
 Pour plus d’informations sur les erreurs susceptibles de survenir lorsque la sérialisation XML, consultez l’article de Support Microsoft suivant : [« Impossible de charger un assembly de sérialisation généré de manière dynamique »](http://support.microsoft.com/kb/913668).  
  
 Pour plus d'informations sur les types de données qui ne sont pas pris en charge par le sérialiseur XML, consultez la rubrique consacrée à la prise en charge de la liaison de schéma XML dans le .NET Framework dans la documentation de ce dernier.  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux données à partir des objets de base de données CLR](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)   
 [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)  
  
  
