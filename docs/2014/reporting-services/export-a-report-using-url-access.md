---
title: Exporter un rapport à l’aide de l’accès URL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- formats [Reporting Services], URL rendering
- URL access [Reporting Services], rendering formats
ms.assetid: 6a3b7fc3-3d91-4d12-8371-42ea12e74517
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b90f1ad3e67aafa2ee8b967f8a04ddb16daf4e53
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48132903"
---
# <a name="export-a-report-using-url-access"></a>Exporter un rapport à l'aide de l'accès URL
  Vous pouvez éventuellement spécifier le format de rendu d’un rapport à l’aide de la *rs : Format* paramètre. Par exemple, pour obtenir une copie PDF d'un rapport directement à partir d'un serveur de rapports en mode natif :  
  
```  
http://myrshost/ReportServer?/myreport&rs:Format=PDF  
```  
  
 Et, pour un serveur de rapport SharePoint en mode intégré :  
  
```  
http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/myrereport.rdl&rs:Format=PDF  
```  
  
 Les valeurs utilisables pour ce paramètre dépendent des extensions de rendu de rapport installées sur le serveur de rapports auquel vous accédez. Les extensions les plus fréquentes sont HTML4.0, WORD, MHTML, IMAGE, EXCEL, CSV, PDF, XML et NULL. Lorsque l'extension de rendu définie n'est pas installée sur le serveur de rapports, le rapport ne peut pas être restitué et le navigateur affiche un message d'erreur.  
  
 Lorsque le paramètre *Format* n'est pas ajouté à l'URL, le serveur de rapports détecte le navigateur requis et restitue le rapport dans le format HTML approprié.  
  
## <a name="see-also"></a>Voir aussi  
 [Accès URL &#40;SSRS&#41;](url-access-ssrs.md)   
 [Référence de paramètres d'accès URL](url-access-parameter-reference.md)  
  
  
