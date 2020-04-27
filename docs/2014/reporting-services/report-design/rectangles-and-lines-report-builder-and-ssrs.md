---
title: Rectangles et lignes (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d6226b0c-0398-4185-8565-96099876fc21
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f447d05501949df0fd0860ed7799fca2932714fa
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66105388"
---
# <a name="rectangles-and-lines-report-builder-and-ssrs"></a>Rectangles et lignes (Générateur de rapports et SSRS)
  Les rectangles et les lignes permettent de créer des effets visuels dans un rapport. Vous pouvez afficher des propriétés sur ces éléments de rapports à partir de la section Bordure sous l'onglet Dossier de base, puis définir d'autres propriétés à l'aide du volet Propriétés. Vous pouvez ajouter des fonctionnalités, telles qu'une couleur ou une image d'arrière-plan, une info-bulle ou un signet, à un rectangle.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="rectangles-and-lines-as-report-parts"></a><a name="RectanglesLinesReportParts"></a> Rectangles et lignes en tant que parties de rapports  
 Vous pouvez publier des rectangles avec les éléments qu'ils contiennent, séparément des rapports, sous forme de parties de rapport. [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 Vous ne pouvez pas publier les éléments de rapport dans le rectangle en tant que parties de rapport. Lorsque des utilisateurs ajoutent le rectangle à un rapport, ils obtiennent le rectangle et les éléments qu'il contient.  
  

  
##  <a name="using-a-rectangle-as-a-container"></a><a name="RectangleAsContainer"></a>Utilisation d’un rectangle comme conteneur  
 Vous pouvez utiliser un rectangle comme conteneur d'autres éléments. Lorsque vous le déplacez, les éléments qu'il contient se déplacent avec lui. Un élément dans le rectangle indique le nom du rectangle dans sa propriété **Parent** . Pour plus d’informations sur l’utilisation d’un rectangle comme conteneur, consultez [Ajouter un rectangle ou un conteneur &#40;Générateur de rapports et SSRS&#41;](add-a-rectangle-or-container-report-builder-and-ssrs.md) et [Afficher les mêmes données dans une matrice et sur un graphique &#40;Générateur de rapports&#41;](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md).  
  
> [!NOTE]  
>  Un rectangle est uniquement un conteneur pour les éléments que vous créez dans le rectangle ou que vous faites glisser dans le rectangle. Si vous dessinez un rectangle autour d'un élément qui existe déjà dans l'aire de conception, le rectangle n'agit pas comme son conteneur. Le rectangle n'est pas répertorié dans la propriété Parent de l'élément.  
  
 Lorsque vous utilisez des rectangles pour contenir des éléments de rapport, réfléchissez comment ces éléments seront affectés dans leur ensemble lors du rendu de rapports. Les éléments de rapports contenant des lignes répétées de données (des tables, par exemple) sont développés pour accueillir les données retournées par une requête. Ceci affecte le positionnement d'autres éléments dans le rectangle. Une table pousse les éléments vers le bas si ceux-ci sont placés sous la région de données. Pour ancrer un élément à sa position, vous pouvez le placer à l'intérieur d'un rectangle dont le bord supérieur est situé au-dessus du bord inférieur de la table. Pour plus d’informations, consultez [Comportements de rendu &#40;Générateur de rapports et SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).  
  

  
##  <a name="adding-a-report-border"></a><a name="ReportBorder"></a> Ajout d'une bordure de rapport  
 Vous pouvez entourer un rapport d'une bordure en plaçant celle-ci dans les en-têtes, les pieds de page et le corps du rapport, sans ajouter de lignes ou de rectangles. Pour plus d’informations, consultez [Ajouter une bordure à un rapport &#40;Générateur de rapports et SSRS&#41;](add-a-border-to-a-report-report-builder-and-ssrs.md).  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a>Rubriques de procédures  
 [Ajouter une bordure à un rapport &#40;Générateur de rapports et SSRS&#41;](add-a-border-to-a-report-report-builder-and-ssrs.md)  
  
 [Ajouter un rectangle ou un conteneur &#40;Générateur de rapports et SSRS&#41;](add-a-rectangle-or-container-report-builder-and-ssrs.md)  
  
 [Ajouter et modifier une ligne &#40;Générateur de rapports et SSRS&#41;](add-and-modify-a-line-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter un rectangle ou un conteneur &#40;Générateur de rapports et SSRS&#41;](add-a-rectangle-or-container-report-builder-and-ssrs.md)  
  
  
