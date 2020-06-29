---
title: Nouveautés de&#39;(Integration Services) | Microsoft Docs
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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 84f0b668407c89e1d6acc3c8cfbda73f129ca19a
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439856"
---
# <a name="what39s-new-integration-services"></a>Nouveautés de&#39;(Integration Services)
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]n’est pas modifié à partir de la version précédente.  
  
 Pour plus d’informations sur les autres [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] produits et technologies, consultez [nouveautés de SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
 Pour plus d’informations sur les modifications associées à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Business Intelligence, consultez [nouveautés de Analysis Services et Business Intelligence](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services).  
  
##  <a name="rich-xml-validation-output-in-the-xml-task"></a><a name="ValidateXML"></a> Sortie de validation XML détaillée dans la tâche XML  
 Validez des documents XML et obtenez une sortie d’erreur détaillée en activant la propriété `ValidationDetails` de la tâche XML. Avant que la propriété `ValidationDetails` ne soit disponible, la validation XML par la tâche XML ne renvoyait qu’un résultat true ou false, sans aucune information sur les erreurs ou leur emplacement. À présent, quand vous définissez `ValidationDetails` sur true, le fichier de sortie contient des informations détaillées sur chaque erreur, notamment le numéro de ligne et la position. Vous pouvez utiliser ces informations pour comprendre, localiser et corriger les erreurs dans les documents XML. Pour plus d’informations, consultez [Validate XML with the XML Task](control-flow/xml-task.md).  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] a introduit la propriété `ValidationDetails` dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 2. Cette nouvelle propriété n’a pas été annoncée ou documentée à ce moment-là. La propriété `ValidationDetails` est également disponible dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] et dans SQL Server 2016.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
