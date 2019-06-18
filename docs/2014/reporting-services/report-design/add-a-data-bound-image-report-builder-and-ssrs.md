---
title: Ajouter une image liée à des données (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: df4c38d4-bfcc-41c4-aa6d-952ca6fd7a2e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2878198caf3db1917c596ff37b7619a5a0597621
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66106903"
---
# <a name="add-a-data-bound-image-report-builder-and-ssrs"></a>Ajouter une image liée à des données (Générateur de rapports et SSRS)
  Un rapport peut inclure une référence à une image stockée dans une base de données. Cette image est appelée *image liée aux données*. Les images qui jouxtent les noms de produits dans une liste de produits sont des exemples d'images liées à des données.  
  
 L'ajout d'une image liée à des données à un en-tête de page ou pied de page requiert des étapes supplémentaires. Pour plus d’informations, consultez [En-têtes et pieds de page &#40;Générateur de rapports et SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-data-bound-image"></a>Pour ajouter une image liée à des données  
  
1.  En mode de conception de rapport, créez une table avec une connexion à la source de données et un dataset avec un champ qui contient des données binaires de type image. Pour plus d’informations, consultez [Tables &#40;Générateur de rapports et SSRS&#41;](tables-report-builder-and-ssrs.md).  
  
2.  Insérez une colonne dans votre table. Pour plus d’informations, consultez [Insérer ou supprimer une colonne &#40;Générateur de rapports et SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).  
  
3.  Dans le menu **Insérer** , cliquez sur **Image**, puis cliquez sur la ligne de données de la nouvelle colonne.  
  
4.  Dans la page Général de la boîte de dialogue **Propriétés de l’image** , tapez un nom dans la zone de texte **Nom** ou acceptez le nom par défaut.  
  
5.  (Facultatif) Dans la zone de texte **Info-bulle** , tapez le texte à afficher quand l’utilisateur pointe sur l’image dans le rapport rendu au format HTML.  
  
6.  Dans **Sélectionner la source de l’image**, sélectionnez **Base de données**.  
  
7.  Dans **Utiliser ce champ**, sélectionnez le champ qui contient des images dans votre rapport.  
  
8.  Dans **Utiliser ce type MIME**, sélectionnez le type MIME ou le format de fichier de l’image, par exemple bmp.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Un espace réservé à l'image apparaît sur l'aire de conception du rapport.  
  
## <a name="see-also"></a>Voir aussi  
 [Images &#40;Générateur de rapports et SSRS&#41;](images-report-builder-and-ssrs.md)   
 [Incorporer une image dans un rapport &#40;Générateur de rapports et SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md)   
 [Ajouter une image externe &#40;Générateur de rapports et SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md)   
 [Boîte de dialogue Propriétés de l’image, Général &#40;Générateur de rapports et SSRS&#41;](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
