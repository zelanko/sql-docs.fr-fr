---
title: Imprimer des rapports à partir d’autres applications (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5560581-fd57-4a45-b7ea-43b21a8a7419
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: cc94d80dd6ba01575ac60319d8a453afb97d6b06
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152985"
---
# <a name="print-reports-from-other-applications-report-builder-and-ssrs"></a>Imprimer des rapports à partir d'autres applications (Générateur de rapport et SSRS)
  Le Générateur de rapports fournit une option d'exportation qui vous permet d'afficher facilement un rapport dans d'autres applications. Le `Export` commande est disponible dans la barre d’outils de rapport qui s’affiche en haut d’un rapport lorsque vous l’ouvrez dans un navigateur ou une application basée sur le Web. L'exportation d'un rapport permet son affichage dans une autre application (par exemple, l'exportation d'un rapport vers Excel permet d'ouvrir le rapport dans [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]). Pour l'impression, l'exportation d'un rapport est recommandée uniquement si l'application dispose de fonctionnalités d'impression spécifiques que vous souhaitez utiliser.  
  
 Pour exporter un rapport vers une autre application, cette dernière doit être installée. Par exemple, Adobe Acrobat Reader doit être préalablement installé sur votre ordinateur si vous choisissez une exportation au format Acrobat (PDF). Si vous choisissez d'exporter un rapport au format TIFF, le serveur de rapports place le rapport dans une application de visualisation associée au type de fichier TIFF. Bien que l'application utilisée dépende de la version de [!INCLUDE[msCoName](../../includes/msconame-md.md)] dont vous disposez, il s'agit généralement de l'outil Aperçu des images et des télécopies Windows. La résolution par défaut correspond à une résolution d'écran de 96 points par pouce (ppp). Vous pouvez augmenter la résolution dans l'outil Aperçu des images et des télécopies Windows à 300 ppp ou à 600 ppp de sorte qu'elle corresponde aux performances de votre imprimante. Pour plus d'informations sur le réglage de la résolution, consultez la documentation du produit Windows.  
  
 Si vous choisissez le format d'archive Web (également appelé MHTML), le rapport est exporté vers votre navigateur par défaut. L'impression à partir du navigateur peut entraîner l'ajout du chemin d'accès du rapport au bas de chaque page. Dans la plupart des cas, vous pouvez définir des options dans le navigateur afin que ces informations ne soient pas imprimées. Pour plus d'informations, consultez la documentation relative au navigateur utilisé.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Imprimer un rapport &#40;Générateur de rapports et SSRS&#41;](print-a-report-report-builder-and-ssrs.md)   
 [Imprimer des rapports à partir d’un navigateur à l’aide du contrôle d’impression &#40;Générateur de rapports et SSRS&#41;](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)   
 [Exportation de rapports &#40;rapport Générateur et SSRS&#41;](export-reports-report-builder-and-ssrs.md)   
 [Exporter un rapport dans un autre type de fichier &#40;Générateur de rapports et SSRS&#41;](../export-a-report-as-another-file-type-report-builder-and-ssrs.md)   
 [Recherche, affichage et gestion de rapports &#40;Générateur de rapports et SSRS&#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  