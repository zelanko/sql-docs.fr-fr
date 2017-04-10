---
title: "T&#233;l&#233;charger un fichier ou un rapport (Gestionnaire de rapports) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "publication de rapports [Reporting Services], chargement de fichiers"
  - "rapports [Reporting Services], publication"
  - "téléchargement de rapports (upload) [Reporting Services]"
  - "téléchargement de fichiers (upload) [Reporting Services]"
  - "fichiers [Reporting Services], chargement"
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
caps.latest.revision: 42
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 42
---
# T&#233;l&#233;charger un fichier ou un rapport (Gestionnaire de rapports)
  Le Gestionnaire de rapports fournit une fonctionnalité de téléchargement qui vous permet d'ajouter des rapports, des modèles et d'autres fichiers à un serveur de rapports sans devoir publier ces éléments à partir d'une application cliente. Les fichiers que vous téléchargez à partir du système de fichiers sont stockés en tant qu'éléments sur le serveur de rapports. Le type de fichier téléchargé détermine son mode de stockage :  
  
-   Les fichiers .rdl sont stockés sous forme de rapports.  
  
-   Les fichiers .smdl sont stockés sous forme de modèles de rapports.  
  
-   Tous les autres fichiers, y compris les fichiers de sources de données partagées (.rds), sont téléchargés en tant que ressources. Les ressources ne sont pas traitées par un serveur de rapports mais peuvent être affichées dans le Gestionnaire de rapports si le serveur de rapports prend en charge le type MIME du fichier.  
  
### Pour télécharger un fichier ou un rapport  
  
1.  Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md).  
  
2.  Dans le Gestionnaire de rapports, parcourez l'arborescence jusqu'à la page **Contenu** . Localisez le dossier auquel ajouter un élément.  
  
3.  Cliquez sur **Télécharger un fichier**.  
  
4.  Cliquez sur **Parcourir** pour sélectionner un fichier à charger sur le serveur. Vous pouvez télécharger un fichier de définition de rapport, une image, un document ou tout autre fichier que vous souhaitez rendre accessible sur le serveur de rapports.  
  
5.  Tapez un nom pour le nouvel élément. Ce nom peut comporter des espaces, mais il ne peut pas contenir les caractères réservés suivants : ; ? : @ & = + , $ / * \< > |.  
  
6.  Pour remplacer un élément existant par le nouveau, sélectionnez **Remplacer l’élément s’il existe**.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## Voir aussi  
 [Créer, supprimer ou modifier une source de données partagée &#40;Gestionnaire de rapports&#41;](../Topic/Create,%20Delete,%20or%20Modify%20a%20Shared%20Data%20Source%20\(Report%20Manager\).md)   
 [Page Contenu &#40;Gestionnaire de rapports&#41;](../Topic/Contents%20Page%20\(Report%20Manager\).md)   
 [Page Télécharger un fichier &#40;Gestionnaire de rapports&#41;](../Topic/Upload%20File%20Page%20\(Report%20Manager\).md)   
 [Télécharger des fichiers dans un dossier](../../reporting-services/report-server/upload-files-to-a-folder.md)  
  
  