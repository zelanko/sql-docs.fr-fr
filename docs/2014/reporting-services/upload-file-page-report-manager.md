---
title: Page télécharger un fichier (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7bb3166f-9374-4449-b66a-ffb77298507d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1100baa3cd72a04d208b2076d91ca4efed7d38e6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66098865"
---
# <a name="upload-file-page-report-manager"></a>Page Télécharger un fichier (Gestionnaire de rapports)
  La page Télécharger un fichier vous permet de publier un fichier du système de fichiers dans la base de données du serveur de rapports. Les fichiers téléchargés sont représentés comme des éléments dans l'arborescence des dossiers du serveur de rapports.  
  
-   Les fichiers .rdl téléchargés sont publiés sur un serveur de rapports sous forme de rapport.  
  
-   Les fichiers .smdl téléchargés sont publiés sous la forme de modèles de rapports s'ils contiennent des informations sur la vue de la source de données. Si une référence de la vue de source de données est absente, une erreur se produit au cours du téléchargement. Certaines informations sur la vue de source de données peuvent être manquantes si vous téléchargez un fichier .smdl à partir d'un projet de modèle de rapport [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Dans les projets de modèles de rapports, les informations de la vue de source de données sont stockées dans un fichier distinct au lieu d'être incluses dans le fichier .smdl lui-même.  
  
     Les fichiers de modèles qui contiennent des informations sur la vue de source de données (et qui peuvent par conséquent être téléchargés) ont été précédemment publiés sur un serveur de rapports, puis enregistrés depuis le serveur dans un fichier du système de fichiers. Si vous ouvrez la page Propriétés générales d'un modèle et cliquez sur **Modifier** pour ouvrir le modèle, vous pouvez enregistrer celui-ci dans un fichier, puis le télécharger sous la forme d'un nouveau modèle sur le serveur de rapports. Le fichier .smdl que vous téléchargez ensuite contient toutes les informations nécessaires à la publication du modèle.  
  
-   Tous les autres types de fichiers que vous téléchargez sont stockés comme des ressources. Cela inclut les fichiers .rds qui contiennent des informations de connexion de la source de données du rapport. Le téléchargement d'un fichier .rds ne produit pas d'élément de source de données partagée sur le serveur de rapports.  
  
 Lorsque vous téléchargez un élément, il est placé dans le dossier actif. Une fois le téléchargement terminé, vous pouvez déplacer l'élément vers un emplacement différent.  
  
> [!NOTE]  
>  Cette fonctionnalité n'est pas disponible dans toutes les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
### <a name="to-open-the-upload-file-page"></a>Pour ouvrir la page Télécharger un fichier  
  
1.  Ouvrez le Gestionnaire de rapports et accédez au dossier dans lequel vous voulez télécharger un fichier.  
  
2.  Dans la barre d'outils, cliquez sur **Télécharger un fichier**.  
  
## <a name="options"></a>Options  
 **Fichier à télécharger**  
 Affiche le chemin d'accès complet au fichier que vous copiez à partir du système de fichiers.  
  
 **Parcourir**  
 Cliquez pour choisir un fichier dans le système de fichiers.  
  
 **Nom**  
 Tapez le nom du fichier tel qu'il apparaîtra dans l'espace de noms du serveur de rapports. Le nom doit contenir un caractère alphanumérique au minimum. Il peut également comporter des espaces et certains symboles. N'utilisez pas les caractères ; ? : \@ & = +, $ * \< > | "ou / lorsque vous spécifiez un nom d’élément.  
  
 **Remplacer l’élément s’il existe**  
 Activez cette case à cocher si vous souhaitez remplacer un élément existant par une nouvelle version. Pour remplacer une version existante, le nom du nouvel élément et celui de l'élément existant doivent être identiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Page Contenu &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/contents-page-report-manager.md)   
 [F1 du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)   
 [Télécharger des fichiers dans un dossier](report-server/upload-files-to-a-folder.md)  
  
  
