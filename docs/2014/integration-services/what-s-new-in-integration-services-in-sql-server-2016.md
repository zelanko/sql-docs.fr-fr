---
title: Ce que&#39;s nouveau (Integration Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, what's new
- what's new [Integration Services]
ms.assetid: da6999c7-e5e3-4a59-a284-1da635995af1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 804e528aed70a6612f35391bd4ad96ebfd03df3a
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52792011"
---
# <a name="what39s-new-integration-services"></a>Ce que&#39;s nouveau (Integration Services)
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] reste inchangé par rapport à la version précédente.  
  
 Pour plus d’informations sur les autres [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] produits et technologies, consultez [What ' s New in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
 Pour plus d’informations sur les modifications liées à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Business Intelligence, consultez [What ' s New in Analysis Services et Business Intelligence](../analysis-services/what-s-new-in-analysis-services.md).  
  
##  <a name="ValidateXML"></a> Sortie de validation XML détaillée dans la tâche XML  
 Validez des documents XML et obtenez une sortie d’erreur détaillée en activant la propriété `ValidationDetails` de la tâche XML. Avant que la propriété `ValidationDetails` ne soit disponible, la validation XML par la tâche XML ne renvoyait qu’un résultat true ou false, sans aucune information sur les erreurs ou leur emplacement. À présent, quand vous définissez `ValidationDetails` sur true, le fichier de sortie contient des informations détaillées sur chaque erreur, notamment le numéro de ligne et la position. Vous pouvez utiliser ces informations pour comprendre, localiser et corriger les erreurs dans les documents XML. Pour plus d’informations, consultez [Validate XML with the XML Task](control-flow/xml-task.md).  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] a introduit la propriété `ValidationDetails` dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 2. Cette nouvelle propriété n’a pas été annoncée ou documentée à ce moment-là. La propriété `ValidationDetails` est également disponible dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] et dans SQL Server 2016.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
