---
title: Effectuer le rendu d’un instantané d’historique de rapports à l’aide de l’accès URL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], report history
- history snapshots [Reporting Services]
- historical data [Reporting Services]
- snapshots [Reporting Services], URL access
- snapshots [Reporting Services], rendering report history
ms.assetid: 3f87f82d-0e61-4492-9c4b-f5238c39e8cd
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: f8b857d0aab5cc64255e3d041d58fdc7ab398358
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48216619"
---
# <a name="render-a-report-history-snapshot-using-url-access"></a>Rendre un instantané d'historique de rapport à l'aide de l'accès URL
  Vous pouvez effectuer le rendu d’un rapport reposant sur une capture instantanée d’historique de rapport en indiquant le paramètre *rs:Snapshot* et en définissant sa valeur sur un ID de capture instantanée valide. La valeur de ce paramètre doit être spécifiée au format AAAA-MM-JJTHH:MM:SS, conformément à la norme ISO 8601.  
  
 Si vous omettez ce paramètre, le rapport est rendu selon le paramétrage des options d'exécution de rapports et de gestion du cache du serveur de rapports. Pour plus d’informations sur l’exécution des rapports, consultez [définir les propriétés de traitement de rapport](report-server/set-report-processing-properties.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre une URL qui extrait un instantané d'historique de rapport :  
  
```  
http://myrshost/reportserver?/SampleReports/Company Sales&rs:Snapshot=2003-04-07T13:40:02  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Accès URL &#40;SSRS&#41;](url-access-ssrs.md)   
 [Référence de paramètres d'accès URL](url-access-parameter-reference.md)  
  
  
