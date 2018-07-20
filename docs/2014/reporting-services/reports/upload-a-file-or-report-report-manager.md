---
title: Télécharger un fichier ou un rapport (Gestionnaire de rapports) | Microsoft Docs
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
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
caps.latest.revision: 41
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 44dd1787da648e332c2234b83323990784b0d4bc
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085441"
---
# <a name="upload-a-file-or-report-report-manager"></a>Télécharger un fichier ou un rapport (Gestionnaire de rapports)
  Le Gestionnaire de rapports fournit une fonctionnalité de téléchargement qui vous permet d'ajouter des rapports, des modèles et d'autres fichiers à un serveur de rapports sans devoir publier ces éléments à partir d'une application cliente. Les fichiers que vous téléchargez à partir du système de fichiers sont stockés en tant qu'éléments sur le serveur de rapports. Le type de fichier téléchargé détermine son mode de stockage :  
  
-   Les fichiers .rdl sont stockés sous forme de rapports.  
  
-   Les fichiers .smdl sont stockés sous forme de modèles de rapports.  
  
-   Tous les autres fichiers, y compris les fichiers de sources de données partagées (.rds), sont téléchargés en tant que ressources. Les ressources ne sont pas traitées par un serveur de rapports mais peuvent être affichées dans le Gestionnaire de rapports si le serveur de rapports prend en charge le type MIME du fichier.  
  
### <a name="to-upload-a-file-or-report"></a>Pour télécharger un fichier ou un rapport  
  
1.  Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Dans le Gestionnaire de rapports, parcourez l'arborescence jusqu'à la page **Contenu** . Localisez le dossier auquel ajouter un élément.  
  
3.  Cliquez sur **Télécharger un fichier**.  
  
4.  Cliquez sur **Parcourir** pour sélectionner un fichier à charger sur le serveur. Vous pouvez télécharger un fichier de définition de rapport, une image, un document ou tout autre fichier que vous souhaitez rendre accessible sur le serveur de rapports.  
  
5.  Tapez un nom pour le nouvel élément. Ce nom peut comporter des espaces, mais il ne peut pas contenir les caractères réservés suivants : ; ? : \@ & = +, $ / * \< > |.  
  
6.  Pour remplacer un élément existant par le nouveau, sélectionnez **Remplacer l’élément s’il existe**.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Créer, supprimer ou modifier une Source de données partagée &#40;le Gestionnaire de rapports&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md)   
 [Contenu de la Page &#40;le Gestionnaire de rapports&#41;](../contents-page-report-manager.md)   
 [Page Charger un fichier &#40;Gestionnaire de rapports&#41;](../upload-file-page-report-manager.md)   
 [Télécharger des fichiers dans un dossier](../report-server/upload-files-to-a-folder.md)  
  
  
