---
title: Exporter un rapport à l’aide de l’accès URL | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- formats [Reporting Services], URL rendering
- URL access [Reporting Services], rendering formats
ms.assetid: 6a3b7fc3-3d91-4d12-8371-42ea12e74517
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bf1113603800d232ccdc88aa6b436f8d8a0e6f6c
ms.sourcegitcommit: 9ece10c2970a4f0812647149d3de2c6b75713e14
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51814202"
---
# <a name="export-a-report-using-url-access"></a>Exporter un rapport à l'aide de l'accès URL
  Vous pouvez éventuellement spécifier le format de rendu du rapport à l’aide du paramètre d’URL *rs:Format* .  Les formats HTML4.0 et HTM5 (extensions de rendu) seront restitués dans le navigateur. Pour les autres formats, le navigateur vous invite à enregistrer la sortie du rapport dans un fichier local.  
  
 Par exemple, pour obtenir une copie PDF d'un rapport directement à partir d'un serveur de rapports en mode natif :  
  
```  
https://myrshost/ReportServer?/myreport&rs:Format=PDF  
```  
  
 Et, pour un serveur de rapport SharePoint en mode intégré :  
  
```  
https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/myrereport.rdl&rs:Format=PDF  
```  
  
 À titre d’exemple, la commande URL suivante dans votre navigateur exporte un rapport PPTX à partir d’une instance nommée du serveur de rapports :  
  
```  
https://servername/ReportServer_THESQLINSTANCE/Pages/ReportViewer.aspx?%2freportfolder%2freport+name+with+spaces&rs:Format=pptx  
```  
  
 Les valeurs utilisables pour ce paramètre dépendent des extensions de rendu de rapport installées sur le serveur de rapports auquel vous accédez. Les extensions les plus fréquentes sont HTML4.0, MHTML, IMAGE, EXCELOPENXML (xlsx), WORDOPENXML (docx), CSV, PDF, XML et NULL. Lorsque l'extension de rendu définie n'est pas installée sur le serveur de rapports, le rapport ne peut pas être restitué et le navigateur affiche un message d'erreur.  
  
 Lorsque le paramètre *Format* n'est pas ajouté à l'URL, le serveur de rapports détecte le navigateur requis et restitue le rapport dans le format HTML approprié.  
  
## <a name="see-also"></a> Voir aussi  
 [Accès URL &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [Référence de paramètre d'accès URL](../reporting-services/url-access-parameter-reference.md)  
  
  
