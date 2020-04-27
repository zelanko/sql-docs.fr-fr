---
title: Boîte de dialogue Propriétés de l’image, général (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10051"
- sql12.rtp.rptdesigner.pictureproperties.general.f1
ms.assetid: c2218b93-f7fe-46ef-995f-d7dadf9752ec
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8a66c424bfe5bd4a2587140a0f5238f46833a061
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109030"
---
# <a name="image-properties-dialog-box-general-report-builder-and-ssrs"></a>Boîte de dialogue Propriétés de l'image, Général (Générateur de rapports et SSRS)
  Sélectionnez **Général** dans la boîte de dialogue **Propriétés de l’image** pour ajouter une image, changer le nom par défaut de l’image et ajouter le texte de l’info-bulle.  
  
## <a name="options"></a>Options  
 **Nom**  
 Tapez le nom de l'élément. Ce nom doit être unique dans le rapport. Par défaut, un nom général, tel qu'Image1 ou Image2, est assigné.  
  
 **Bulle**  
 Tapez du texte ou une expression qui se transforme en info-bulle. Cliquez sur le bouton Expression (*fx*) pour modifier l’expression. L’ **info-bulle** apparaît quand l’utilisateur place le pointeur sur l’élément dans un rapport HTML.  
  
 **Sélectionner la source de l'image**  
 Indiquez l'endroit où l'image est stockée afin que lorsque le rapport est rendu, le processeur de rapports sache où la chercher.  
  
-   **Externe** Choisissez cette option lorsque vous souhaitez que l'image continue à exister sous la forme d'un fichier sur un serveur de rapports ou un serveur Web.  
  
-   **Rapport** Choisissez cette option lorsque vous souhaitez incorporer l’image dans le rapport.  
  
-   **Base de données** Choisissez cette option lorsque vous souhaitez inclure un nom de champ de base de données qui représente les images que vous souhaitez inclure dans votre rapport.  
  
 **Utiliser cette image**  
 Cette option s’affiche quand vous sélectionnez l’option **Rapport** ou **Externe** .  
  
 Si vous incorporez l'image, choisissez l'image que vous souhaitez ajouter au rapport dans la liste déroulante. Cliquez sur le bouton **Importer** pour ajouter l’image à la liste déroulante.  
  
 Si vous sélectionnez l'option **Externe** , tapez l'URL de l'image. Pour un rapport publié sur un serveur de rapports configuré pour le mode natif, utilisez un chemin d'accès complet ou relatif. Par exemple, http://\<ServerName>/images/image1.jpg. Pour un rapport publié sur un serveur de rapports configuré en mode intégré SharePoint, utilisez une URL complète. Par exemple, http://\<*SharePointservername*>/\<*site*>/documents/images/image1.jpg.  
  
 **Importer**  
 Cliquez pour ajouter une image à la liste déroulante **Utiliser cette image** .  
  
 **Utiliser ce champ**  
 Cette option apparaît si vous avez sélectionné l’option **Base de données** . Sélectionnez le nom du champ.  
  
 **Utiliser ce type MIME**  
 Choisissez le format approprié des images contenues dans la base de données, par exemple .bmp, .jpeg, .gif, .png et .x-png.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)   
 [Images &#40;Générateur de rapports et SSRS&#41;](report-design/images-report-builder-and-ssrs.md)   
 [Aide du Générateur de rapports pour les boîtes de dialogue, les volets et les Assistants](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)  
  
  
