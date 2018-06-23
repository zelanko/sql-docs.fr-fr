---
title: Effectuer le rendu d’un instantané d’historique de rapports à l’aide de l’accès URL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- URL access [Reporting Services], report history
- history snapshots [Reporting Services]
- historical data [Reporting Services]
- snapshots [Reporting Services], URL access
- snapshots [Reporting Services], rendering report history
ms.assetid: 3f87f82d-0e61-4492-9c4b-f5238c39e8cd
caps.latest.revision: 32
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 29ff943923807b88db27bd9c8c6a1cc8430f96a3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139529"
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
  
  