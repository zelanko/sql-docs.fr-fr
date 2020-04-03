---
title: Charger un fichier ou un rapport dans le serveur de rapports | Microsoft Docs
description: Découvrez comment ajouter des rapports et d’autres fichiers à un serveur de rapports sans avoir à les publier à partir d’une application cliente.
ms.date: 05/24/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 6d5d70a2147ea5cb9846ed37ea8963cc8c3f98e3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "79510050"
---
# <a name="upload-a-file-or-report-in-the-report-server"></a>Charger un fichier ou un rapport dans le serveur de rapports
Le portail web du serveur de rapports fournit une fonctionnalité de chargement qui vous permet d’ajouter des rapports et d’autres fichiers à un serveur de rapports sans devoir publier ces éléments à partir d’une application cliente. Les fichiers que vous téléchargez à partir du système de fichiers sont stockés en tant qu'éléments sur le serveur de rapports. Le type de fichier téléchargé détermine son mode de stockage :  
  
-   Les fichiers .rdl sont stockés sous forme de rapports paginés.  
  
-   Tous les autres fichiers, y compris les fichiers de sources de données partagées (.rds), sont téléchargés en tant que ressources. Les ressources ne sont pas traitées par un serveur de rapports, mais peuvent être affichées dans le portail web si le serveur de rapports prend en charge le type MIME du fichier.  
  
### <a name="to-upload-a-file-or-report"></a>Pour télécharger un fichier ou un rapport  
  
1.  Dans le portail web, cliquez sur **Charger**.  
  
4.  Accédez au fichier à charger. Vous pouvez télécharger un fichier de définition de rapport, une image, un document ou tout autre fichier que vous souhaitez rendre accessible sur le serveur de rapports.  
  
5.  Tapez un nom pour le nouvel élément. Un nom d’élément peut comporter des espaces, mais il ne peut pas contenir les caractères réservés : \; \? \: \@ \& \= \+ \, \$ \/ \* \< \> \|.  
  
6.  Pour remplacer un élément existant par le nouveau, sélectionnez **Remplacer l’élément s’il existe**.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi   
[Créer, modifier et supprimer des sources de données partagées](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)
[Charger des fichiers dans un dossier](../../reporting-services/report-server/upload-files-to-a-folder.md)  
  
  
