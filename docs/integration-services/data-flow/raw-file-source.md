---
title: Source de fichier brut | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.rawfilesource.f1
- sql13.dts.designer.rawfilesourceconnectionmanager.f1
- sql13.dts.designer.rawfilesourcecolumns.f1
helpviewer_keywords:
- sources [Integration Services], Raw File
- raw data [Integration Services]
- Raw File source
ms.assetid: 5b4daea5-7f76-4674-aa77-0a79f9f97f7d
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 8c65fe330869f5059fdce928bd529141505f4298
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68034356"
---
# <a name="raw-file-source"></a>source de fichier brut

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  La source de fichier brut lit des données brutes dans un fichier. La représentation des données étant native pour la source, celles-ci ne nécessitent aucune traduction et pratiquement aucune analyse. Par conséquent, la source de fichier brut peut lire les données plus rapidement que les autres sources telles que la source du fichier plat et la source OLE DB.  
  
 La source de fichier brut permet d'extraire des données brutes précédemment écrites par la destination de fichier brut. Vous pouvez également faire pointer la source de fichier brut vers un fichier brut vide qui contient uniquement les colonnes (fichier réservé aux métadonnées). Utilisez la destination de fichier brut pour générer le fichier réservé aux métadonnées sans avoir à exécuter le package. Pour plus d’informations, consultez [Destination de fichier brut](../../integration-services/data-flow/raw-file-destination.md).  
  
 Le format de fichier brut contient les informations de tri. La destination de fichier brut enregistre toutes les informations de tri, y compris les indicateurs de comparaison des colonnes de chaîne. La source de fichier brut lit et applique les informations de tri. Vous avez la possibilité de configurer la source de fichier brut pour ignorer les indicateurs de tri du fichier, à l'aide de l'éditeur avancé. Pour plus d’informations sur les indicateurs de comparaison, consultez [Comparaison des données chaîne](../../integration-services/data-flow/comparing-string-data.md).  
  
 Pour configurer le fichier brut, vous spécifiez le nom du fichier lu par la source de fichier brut.  
  
> [!NOTE]  
>  Cette source n'utilise pas de gestionnaire de connexions.  
  
 Cette source a une sortie. Elle ne prend pas en charge de sortie d'erreur.  
  
## <a name="configuration-of-the-raw-file-source"></a>Configuration de la source de fichier brut  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Propriétés personnalisées des fichiers bruts](../../integration-services/data-flow/raw-file-custom-properties.md)  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur la définition des propriétés du composant, consultez [Définir les propriétés d’un composant de flux de données](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="related-content"></a>Contenu associé  
  
-   Entrée de blog, [Raw Files Are Awesome](https://www.sqlservercentral.com/blogs/stratesql/archive/2011/1/1/31-days-of-ssis-_1320_-raw-files-are-awesome-_2800_1_2F00_31_2900_.aspx), sur sqlservercentral.com  
  
## <a name="raw-file-source-editor-connection-manager-page"></a>Éditeur de source de fichier brut (page Gestionnaire de connexions)
  La source de fichier brut lit des données brutes dans un fichier. La représentation des données étant native pour la source, celles-ci ne nécessitent aucune traduction et pratiquement aucune analyse.   
## <a name="raw-file-source-editor-columns-page"></a>Éditeur de source de fichier brut (page Colonnes)
  La source de fichier brut lit des données brutes dans un fichier. La représentation des données étant native pour la source, celles-ci ne nécessitent aucune traduction et pratiquement aucune analyse.   
## <a name="see-also"></a>Voir aussi  
 [Destination de fichier brut](../../integration-services/data-flow/raw-file-destination.md)   
 [Flux de données](../../integration-services/data-flow/data-flow.md)  
  
  
