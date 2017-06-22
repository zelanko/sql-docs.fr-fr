---
title: "Télécharger un fichier ou un rapport (Gestionnaire de rapports) | Documents Microsoft"
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
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
caps.latest.revision: 42
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 227bef646204cd18d2e96a33d398f00a5bbad314
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="upload-a-file-or-report-report-manager"></a>Télécharger un fichier ou un rapport (Gestionnaire de rapports)
  Le Gestionnaire de rapports fournit une fonctionnalité de téléchargement qui vous permet d'ajouter des rapports, des modèles et d'autres fichiers à un serveur de rapports sans devoir publier ces éléments à partir d'une application cliente. Les fichiers que vous téléchargez à partir du système de fichiers sont stockés en tant qu'éléments sur le serveur de rapports. Le type de fichier téléchargé détermine son mode de stockage :  
  
-   Les fichiers .rdl sont stockés sous forme de rapports.  
  
-   Les fichiers .smdl sont stockés sous forme de modèles de rapports.  
  
-   Tous les autres fichiers, y compris les fichiers de sources de données partagées (.rds), sont téléchargés en tant que ressources. Les ressources ne sont pas traitées par un serveur de rapports mais peuvent être affichées dans le Gestionnaire de rapports si le serveur de rapports prend en charge le type MIME du fichier.  
  
### <a name="to-upload-a-file-or-report"></a>Pour télécharger un fichier ou un rapport  
  
1.  Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896).  
  
2.  Dans le Gestionnaire de rapports, parcourez l'arborescence jusqu'à la page **Contenu** . Localisez le dossier auquel ajouter un élément.  
  
3.  Cliquez sur **Télécharger un fichier**.  
  
4.  Cliquez sur **Parcourir** pour sélectionner un fichier à charger sur le serveur. Vous pouvez télécharger un fichier de définition de rapport, une image, un document ou tout autre fichier que vous souhaitez rendre accessible sur le serveur de rapports.  
  
5.  Tapez un nom pour le nouvel élément. Ce nom peut comporter des espaces, mais il ne peut pas contenir les caractères réservés suivants : ; ? : @ & = + , $ / * < > |.  
  
6.  Pour remplacer un élément existant par le nouveau, sélectionnez **Remplacer l’élément s’il existe**.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Créer, supprimer ou modifier une source de données partagée &#40;Gestionnaire de rapports&#41;](http://msdn.microsoft.com/library/cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2)   
 [Page Contenu &#40;Gestionnaire de rapports&#41;](http://msdn.microsoft.com/library/6b16869b-158a-4934-9c85-bee934b35378)   
 [Page Télécharger un fichier &#40;Gestionnaire de rapports&#41;](http://msdn.microsoft.com/library/7bb3166f-9374-4449-b66a-ffb77298507d)   
 [Télécharger des fichiers dans un dossier](../../reporting-services/report-server/upload-files-to-a-folder.md)  
  
  

