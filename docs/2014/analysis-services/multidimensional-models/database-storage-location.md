---
title: Emplacement de stockage de base de données | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- databases [Analysis Services], storage location
ms.assetid: cf88c62e-581e-42f2-846f-a9bf1d7c3292
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1b7c62d96993f1103a216e378bdf89d7b1cdf4ac
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154483"
---
# <a name="database-storage-location"></a>Emplacement de stockage de la base de données
  Il existe souvent des situations où un administrateur de base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (dba) souhaite qu'une certaine base de données réside en dehors du dossier des données du serveur. Ces situations sont souvent générées par des exigences opérationnelles, telles que l'amélioration des performances ou le développement du stockage. Pour ces situations, le `DbStorageLocation` active de la propriété de base de données le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dba pour spécifier l’emplacement de la base de données dans un périphérique de disque ou réseau local.  
  
## <a name="dbstoragelocation-database-property"></a>Propriété de base de données DbStorageLocation  
 Le `DbStorageLocation` propriété de base de données spécifie le dossier dans lequel [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] crée et gère tous les fichiers données et métadonnées de base de données. Tous les fichiers de métadonnées sont stockés sur le `DbStorageLocation` dossier, à l’exception du fichier de métadonnées de base de données, qui est stocké dans le dossier de données du serveur. Il existe deux considérations importantes lors de la définition de la valeur de `DbStorageLocation` propriété de base de données :  
  
-   Le `DbStorageLocation` propriété de base de données doit être définie à un chemin d’accès de dossier UNC existant ou une chaîne vide. Une chaîne vide est la valeur par défaut pour le dossier de données de serveur. Si le dossier n'existe pas, une erreur est déclenchée lorsque vous exécutez une commande `Create`, `Attach` ou `Alter`.  
  
-   Le `DbStorageLocation` propriété de base de données ne peut pas être définie pour pointer vers le dossier de données de serveur ou l’un de ses sous-dossiers. Si l'emplacement pointe sur le dossier de données de serveur ou l'un de ses sous-dossiers, une erreur est déclenchée lorsque vous exécutez une commande `Create`, `Attach` ou `Alter`.  
  
> [!IMPORTANT]  
>  Nous vous recommandons de définir votre chemin d'accès UNC pour l'utilisation d'un réseau de zone de stockage (SAN), d'un réseau basé sur iSCSI ou d'un disque attaché localement. Tout chemin d'accès UNC menant à un partage réseau ou toute solution de stockage à distance à latence élevée conduit à une installation non prise en charge.  
  
### <a name="dbstoragelocation-compared-to-storagelocation"></a>Comparaison entre DbStorageLocation et StorageLocation  
 `DbStorageLocation` spécifie le dossier où réside l'ensemble des données de base de données et des fichiers de métadonnées, alors que `StorageLocation` spécifie le dossier où se trouvent la ou les partitions d'un cube. `StorageLocation` peut être défini indépendamment de `DbStorageLocation`. Il s’agit d’une décision du dba [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fondée sur les résultats attendus et, dans de nombreux cas, les utilisations d’une propriété ou d’une autre se chevauchent.  
  
## <a name="dbstoragelocation-usage"></a>Utilisation de DbStorageLocation  
 Le `DbStorageLocation` propriété de base de données est utilisée en tant que partie d’un `Create` commande dans la base de données un `Detach` / `Attach` de séquence de commandes de base de données, dans un `Backup` / `Restore` séquence de commandes de base de données , ou dans un `Synchronize` commande de base de données. La modification de la propriété de base de données `DbStorageLocation` est considérée comme modification structurelle de l'objet de base de données. Toutes les métadonnées doivent alors être recréées et les données traitées à nouveau.  
  
> [!IMPORTANT]  
>  Vous ne devez pas modifier l'emplacement de stockage de base de données en utilisant une commande `Alter`. Au lieu de cela, nous vous recommandons d’utiliser une séquence de `Detach` / `Attach` commandes de base de données (voir [déplacer une base de données Analysis Services](move-an-analysis-services-database.md), [attacher et détacher Analysis Services bases de données](attach-and-detach-analysis-services-databases.md)).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Attacher et détacher des bases de données Analysis Services](attach-and-detach-analysis-services-databases.md)   
 [Déplacer une base de données Analysis Services](move-an-analysis-services-database.md)   
 [Élément DbStorageLocation](../xmla/xml-elements-properties/dbstoragelocation-element.md)   
 [Créer l’élément &#40;XMLA&#41;](../xmla/xml-elements-commands/create-element-xmla.md)   
 [Élément Attach](../xmla/xml-elements-commands/attach-element.md)   
 [Élément Synchronize &#40;XMLA&#41;](../xmla/xml-elements-commands/synchronize-element-xmla.md)  
  
  