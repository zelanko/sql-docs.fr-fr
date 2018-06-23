---
title: Ce que&#39;s nouvelle (Integration Services) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Integration Services, what's new
- what's new [Integration Services]
ms.assetid: da6999c7-e5e3-4a59-a284-1da635995af1
caps.latest.revision: 112
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c7d37fb3c1d2cd1dcafecc012fbe83e1864e50ed
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039758"
---
# <a name="what39s-new-integration-services"></a>Ce que&#39;s nouvelle (Integration Services)
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] reste inchangé par rapport à la version précédente.  
  
 Pour plus d’informations sur les autres [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] les produits et technologies, consultez [Nouveautés de SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
 Pour plus d’informations sur les modifications apportées lié [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Business Intelligence, consultez [Nouveautés dans Analysis Services et Business Intelligence](../analysis-services/what-s-new-in-analysis-services.md).  
  
##  <a name="ValidateXML"></a> Sortie de validation XML détaillée dans la tâche XML  
 Valider des documents XML et obtenez la sortie d’erreur détaillée en activant le `ValidationDetails` propriété de la tâche XML. Avant du `ValidationDetails` propriété n’était pas disponible, la validation XML par la tâche XML retournée uniquement un résultat true ou false, sans aucune information sur les erreurs ou leur emplacement. Désormais, lorsque vous définissez `ValidationDetails` sur true, la sortie de fichier contient des informations détaillées sur chaque erreur, notamment le numéro de ligne et la position. Vous pouvez utiliser ces informations pour comprendre, localiser et corriger les erreurs dans les documents XML. Pour plus d’informations, consultez [Validate XML with the XML Task](control-flow/xml-task.md).  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] a introduit le `ValidationDetails` propriété [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 2. Cette nouvelle propriété n’a pas été annoncée ou documentée à ce moment-là. Le `ValidationDetails` propriété est également disponible dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] et dans SQL Server 2016.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  