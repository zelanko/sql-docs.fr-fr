---
title: Mettre à jour une ressource (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- updating resources
- resources [Reporting Services], updating
ms.assetid: d21f7493-bcf7-4e9e-9886-55ebdc1f1037
caps.latest.revision: 16
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 0b4fd1def743928ef113b732fac0fde630c0b7d6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328959"
---
# <a name="update-a-resource-report-manager"></a>mise à jour d'une ressource (Gestionnaire de rapports)
  Vous pouvez mettre à jour une ressource en la remplaçant par une nouvelle version. Les ressources sont des éléments stockés sur un serveur de rapports qui tirent leur contenu des fichiers que vous téléchargez. Vous pouvez remplacer une ressource existante en important du contenu de fichier inédit ou différent dans la ressource existante. La mise à jour d'une ressource permet d'actualiser du contenu tout en préservant les propriétés existantes et les paramètres de sécurité définis sur la ressource.  
  
### <a name="to-update-a-resource"></a>Pour mettre à jour une ressource  
  
1.  Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Dans le Gestionnaire de rapports, parcourez l'arborescence jusqu'à la ressource à mettre à jour ou effectuez une recherche pour la localiser.  
  
3.  Cliquez sur la ressource pour l’ouvrir dans la page **Vue** .  
  
4.  Cliquez sur **Propriétés** pour ouvrir la page de propriétés **Général** .  
  
5.  Cliquez sur **Remplacer** pour ouvrir la page **Importer une ressource** .  
  
6.  Cliquez sur **Parcourir**.  
  
7.  Sélectionnez le fichier que vous voulez substituer à la ressource actuelle. Vous pouvez utiliser une version mise à jour du fichier de ressources ou spécifier un fichier avec un nom ou un type de fichier différent.  
  
8.  Cliquez sur **OK** pour charger le fichier de ressources, fermez la page **Importer une ressource** et enregistrez les modifications sur le serveur de rapports.  
  
 Si la ressource en cours de mise à jour contient une image utilisée dans un rapport, vous devez actualiser le rapport pour afficher l'image mise à jour.  
  
## <a name="see-also"></a>Voir aussi  
 [Contenu de la Page &#40;le Gestionnaire de rapports&#41;](../contents-page-report-manager.md)   
 [Page Charger un fichier &#40;Gestionnaire de rapports&#41;](../upload-file-page-report-manager.md)   
 [Télécharger des fichiers dans un dossier](upload-files-to-a-folder.md)   
 [Aide (F1) du Gestionnaire de rapports](../report-manager-f1-help.md)  
  
  
