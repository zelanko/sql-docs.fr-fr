---
title: Remplissez la boîte de dialogue (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.reportbody.fill.f1
- "10065"
- "10501"
- sql12.rtp.rptdesigner.shared.filldv.f1
- sql12.rtp.rptdesigner.rectangleproperties.fill.f1
- "10064"
- sql12.rtp.rptdesigner.textboxproperties.fill.f1
- "10124"
ms.assetid: 93a91d02-d558-4a0e-8d17-3fdf21e208d3
author: maggiesmsft
ms.author: maghan
manager: kfile
ms.openlocfilehash: 08451c74c9227fa76eb78c695908d96066015361
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56018221"
---
# <a name="fill-dialog-box-report-builder-and-ssrs"></a>Boîte de dialogue Remplissage (Générateur de rapports et SSRS)
  Sous l'onglet **Remplissage** , vous pouvez spécifier les options de couleur de l'arrière-plan d'une seule cellule ou de plusieurs cellules dans une région de données ou une zone de texte.  
  
## <a name="options"></a>Options  
 **Couleur de remplissage**  
 Cliquez sur le bouton de couleur pour sélectionner une couleur de remplissage pour le rectangle. Cliquez sur le bouton **Expression**_(fx)_ pour modifier l’expression, qui peut être une valeur hexadécimale pour la couleur RVB ou l’un des noms de couleur prédéfinis fournis dans la boîte de dialogue **Expression** . Pour afficher la liste des couleurs prédéfinies, sélectionnez **Web** dans le volet **Élément**. Les noms de couleur répertoriés dans le volet **Titre** peuvent être tapés dans le volet de texte de l'expression. N'utilisez pas de signe égal (=) ou de guillemets ("") lorsque vous tapez le nom de couleur.  
  
 **Sélectionnez la source d’image**  
 Indiquez l'endroit où l'image est stockée afin que lorsque le rapport est rendu, le processeur de rapports puisse l'afficher.  
  
-   **Externe** Choisissez cette option lorsque vous souhaitez que l'image continue à exister sous la forme d'un fichier sur un serveur de rapports ou un serveur Web.  
  
-   **Rapport** Choisissez cette option lorsque vous souhaitez incorporer l’image dans le rapport.  
  
-   **Base de données** Choisissez cette option lorsque vous souhaitez inclure un nom de champ de base de données qui représente les images que vous souhaitez inclure dans votre rapport.  
  
 **Utiliser cette image**  
 Cette option s’affiche quand vous sélectionnez l’option **Rapport** ou **Externe** .  
  
 Si vous incorporez l’image, choisissez dans la liste déroulante l’image à ajouter au rapport. Cliquez sur **Importer** pour ajouter l’image à la liste déroulante. Si vous avez ajouté une image au volet **Données** , vous pouvez la sélectionner en choisissant **Rapport** , puis en sélectionnant l’image dans la liste déroulante.  
  
 Si vous sélectionnez l'option **Externe** , tapez l'URL de l'image. Pour un rapport publié sur un serveur de rapports configuré en mode natif, utilisez un chemin d’accès complet ou relatif (par exemple, http://*\<nom_serveur >*/images/image1.jpg). Pour un rapport publié sur un serveur de rapports configuré en mode intégré SharePoint, utilisez une URL qualifiée complète (par exemple, http://*\<Nom_serveur_sharepoint > /\<site >*  /Documents/images / Image1.jpg).  
  
 **Importer**  
 Disponible quand vous sélectionnez **Rapport**. Cliquez pour ajouter une image à la liste déroulante **Utiliser cette image** .  
  
 **Utilisez ce champ**  
 Disponible quand vous sélectionnez **Base de données**. Sélectionnez le nom du champ.  
  
 **Utilisez ce type MIME**  
 Choisissez le format approprié des images contenues dans la base de données (par exemple .bmp, .jpeg, .gif, .png ou .x-png).  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme des éléments de rapport &#40;Générateur de rapports et SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md)   
 [Mise en forme du texte et des espaces réservés &#40;Générateur de rapports et SSRS&#41;](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md)   
 [Images &#40;Générateur de rapports et SSRS&#41;](report-design/images-report-builder-and-ssrs.md)  
  
  
