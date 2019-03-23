---
title: Source de fichier brut | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfilesource.f1
helpviewer_keywords:
- sources [Integration Services], Raw File
- raw data [Integration Services]
- Raw File source
ms.assetid: 5b4daea5-7f76-4674-aa77-0a79f9f97f7d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 1bedefd277f1be7f44d807e6539097dd24f5ab2f
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58380752"
---
# <a name="raw-file-source"></a>source de fichier brut
  La source de fichier brut lit des données brutes dans un fichier. La représentation des données étant native pour la source, celles-ci ne nécessitent aucune traduction et pratiquement aucune analyse. Par conséquent, la source de fichier brut peut lire les données plus rapidement que les autres sources telles que la source du fichier plat et la source OLE DB.  
  
 La source de fichier brut permet d'extraire des données brutes précédemment écrites par la destination de fichier brut. Vous pouvez également faire pointer la source de fichier brut vers un fichier brut vide qui contient uniquement les colonnes (fichier réservé aux métadonnées). Utilisez la destination de fichier brut pour générer le fichier réservé aux métadonnées sans avoir à exécuter le package. Pour plus d’informations, consultez [Destination de fichier brut](raw-file-destination.md).  
  
 Le format de fichier brut contient les informations de tri. La destination de fichier brut enregistre toutes les informations de tri, y compris les indicateurs de comparaison des colonnes de chaîne. La source de fichier brut lit et applique les informations de tri. Vous avez la possibilité de configurer la source de fichier brut pour ignorer les indicateurs de tri du fichier, à l'aide de l'éditeur avancé. Pour plus d’informations sur les indicateurs de comparaison, consultez [Comparaison des données chaîne](comparing-string-data.md).  
  
 Pour configurer le fichier brut, vous spécifiez le nom du fichier lu par la source de fichier brut.  
  
> [!NOTE]  
>  Cette source n'utilise pas de gestionnaire de connexions.  
  
 Cette source a une sortie. Elle ne prend pas en charge de sortie d'erreur.  
  
## <a name="configuration-of-the-raw-file-source"></a>Configuration de la source de fichier brut  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../common-properties.md)  
  
-   [Propriétés personnalisées des fichiers bruts](raw-file-custom-properties.md)  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur la définition des propriétés du composant, consultez [Définir les propriétés d’un composant de flux de données](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="related-content"></a>Contenu associé  
  
-   Entrée de blog, [Raw Files Are Awesome](http://www.sqlservercentral.com/blogs/stratesql/archive/2011/1/1/31-days-of-ssis-_1320_-raw-files-are-awesome-_2800_1_2F00_31_2900_.aspx), sur sqlservercentral.com  
  
## <a name="see-also"></a>Voir aussi  
 [Destination de fichier brut](raw-file-destination.md)   
 [Flux de données](data-flow.md)  
  
  
