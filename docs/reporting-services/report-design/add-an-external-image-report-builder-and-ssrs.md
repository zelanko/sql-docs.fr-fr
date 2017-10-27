---
title: "Ajouter une Image externe (Générateur de rapports et SSRS) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81fd4a1f-79a9-4967-86d6-6229413c0995
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 291a906484a6f7d812d091252802b706d207a69e
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="add-an-external-image-report-builder-and-ssrs"></a>Ajouter une image externe (Générateur de rapports et SSRS)
  Les images externes peuvent se trouver sur un serveur de rapports en mode natif ou en mode intégré SharePoint, ou sur un autre site Web. Lorsque vous incluez des images externes dans votre rapport, vous devez vous assurer que l'image existe et que le lecteur du rapport a les autorisations nécessaires pour y accéder. Pour plus d’informations, consultez [Images &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/images-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-external-image"></a>Pour ajouter une image externe  
  
1.  En mode de conception de rapport, sous l’onglet **Insérer** , cliquez sur **Image**.  
  
2.  Cliquez sur l'aire de conception, puis faites glisser la souris pour créer une zone de la taille voulue pour l'image.  
  
3.  Sous l’onglet **Général** de la boîte de dialogue **Propriétés de l’image** , tapez un nom dans la zone de texte **Nom** ou acceptez le nom par défaut.  
  
4.  (Facultatif) Dans la zone de texte **Info-bulle** , tapez le texte à afficher quand l’utilisateur pointe sur l’image dans un rapport rendu au format HTML.  
  
5.  Dans **Sélectionner la source de l’image**, sélectionnez **Externe**.  
  
     Pour une image située sur un serveur de rapports en mode natif, tapez le chemin d’accès relatif de l’image dans la zone **Utiliser cette image**, par exemple ../images/image1.jpg.  
  
     Pour une image sur un serveur de rapports en mode intégré SharePoint, ou un autre site Web, tapez une URL complète vers l’image dans le **utiliser cette image** zone, par exemple, http://\<nom du serveur SharePoint > /\<site > / Documents/images/image1.jpg.  
  
     Pour plus d’informations, consultez [Spécification de chemins d’accès à des éléments externes &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md).  
  
6.  (Facultatif) Cliquez sur **Taille**, **Visibilité**, **Action** ou **Bordure** pour définir des propriétés supplémentaires pour l’élément de rapport de type image.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Incorporer une Image dans un rapport &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md)   
 [Ajouter une Image d’arrière-plan &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/add-a-background-image-report-builder-and-ssrs.md)   
 [Boîte de dialogue des propriétés image, général &#40; Le Générateur de rapports et SSRS &#41;](http://msdn.microsoft.com/library/c2218b93-f7fe-46ef-995f-d7dadf9752ec)  
  
  

