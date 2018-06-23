---
title: Sérialisation XML à partir des objets de base de données CLR | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- serialization
- XML serialization [CLR integration]
- common language runtime [SQL Server], XML serialization
- XmlSerializer class
ms.assetid: ac84339b-9384-4710-bebc-01607864a344
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ad6b9ebaba9f05b0a927cd65f788cdbdb672a6d5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155098"
---
# <a name="xml-serialization-from-clr-database-objects"></a>Sérialisation XML à partir d'objets de base de données CLR
  La sérialisation XML est nécessaire dans deux scénarios :  
  
-   Appel de services Web à partir d'objets CLR (Common Language Runtime).  
  
-   Conversion d'un type défini par l'utilisateur (UDT) en XML.  
  
 La sérialisation XML réalisée par appel de la classe `XmlSerializer` génère normalement un assembly de sérialisation supplémentaire qui est surchargé dans le projet avec l'assembly source. Toutefois, pour des raisons de sécurité, cette surcharge est désactivée dans le CLR. Par conséquent, pour appeler un service web ou d’effectuer une conversion à partir de l’UDT en XML à l’intérieur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l’assembly doit être créé manuellement à l’aide d’un outil appelé **Sgen.exe** fourni avec le .NET Framework qui génère les nécessaires assemblys de sérialisation. Lors de l'appel de `XmlSerializer`, l'assembly de sérialisation doit être créé manuellement en procédant comme suit :  
  
1.  Exécutez le **Sgen.exe** outil qui est fourni avec le SDK .NET Framework pour créer l’assembly qui contient les sérialiseurs XML de l’assembly source.  
  
2.  Inscrivez l'assembly généré dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de l'instruction `CREATE ASSEMBLY`.  
  
 Pour plus d’informations sur les erreurs susceptibles de survenir lorsque la sérialisation XML, consultez l’article de Support technique Microsoft suivant : [« Impossible de charger l’assembly de sérialisation généré de manière dynamique »](http://support.microsoft.com/kb/913668).  
  
 Pour plus d'informations sur les types de données qui ne sont pas pris en charge par le sérialiseur XML, consultez la rubrique consacrée à la prise en charge de la liaison de schéma XML dans le .NET Framework dans la documentation de ce dernier.  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux données depuis les objets de base de données CLR](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)   
 [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)  
  
  
