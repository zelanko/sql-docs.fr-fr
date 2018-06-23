---
title: Schéma de FileTable | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-blob
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FileTables [SQL Server], table schema
ms.assetid: e1cb3880-cfda-40ac-91fc-d08998287f44
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 8515d78ddab2dd39e223087a44b0e021a5aca439
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155065"
---
# <a name="filetable-schema"></a>Schéma de FileTable
  Décrit le schéma prédéfini et fixe d'un FileTable.  
  
|Nom d'attribut de fichier|Type|Taille|Valeur par défaut|Description|Accessibilité du système de fichiers|  
|-------------------------|----------|----------|-------------|-----------------|-------------------------------|  
|**path_locator**|`hierarchyid`|variable|Un `hierarchyid` qui identifie la position de cet élément.|Position de ce nœud dans le FileNamespace hiérarchique.<br /><br /> Clé primaire de la table|Peut être créée et modifiée en définissant les valeurs de chemin d'accès Windows.|  
|**stream_id**|**[uniqueidentifier] rowguidcol**||Une valeur renvoyée par le `NEWID()` (fonction).|ID unique pour les données FILESTREAM.|Non applicable.|  
|**file_stream**|`varbinary(max)`<br /><br /> `filestream`|variable|NULL|Contient les données FILESTREAM.|Non applicable.|  
|**file_type**|`nvarchar(255)`|variable|NULL.<br /><br /> Une opération de création ou de changement de nom dans le système de fichiers remplit la valeur d'extension du fichier à partir du nom.|Représente le type du fichier.<br /><br /> Cette colonne peut être utilisée comme `TYPE COLUMN` lorsque vous créez un index de recherche en texte intégral.<br /><br /> **file_type** est une colonne calculée persistante.|Calculé automatiquement. Ne peut pas être définie.|  
|**Nom**|`nvarchar(255)`|variable|Valeur GUID.|Nom du fichier ou du répertoire.|Peut être créé ou modifié à l'aide des API Windows.|  
|**parent_path_locator**|`hierarchyid`|variable|`hierarchyid` qui identifie le répertoire qui contient cet élément.|Le `hierarchyid` du répertoire conteneur.<br /><br /> **parent_path_locator** est une colonne calculée persistante.|Calculé automatiquement. Ne peut pas être définie.|  
|**cached_file_size**|`bigint`|||Taille des données FILESTREAM, en octets.<br /><br /> **cached_file_size** est une colonne calculée persistante.|Bien que la taille du fichier mis en cache soit automatiquement mise à jour, elle peut être mal synchronisée dans des circonstances exceptionnelles. Pour calculer la taille exacte, utilisez la `DATALENGTH()` (fonction).|  
|**creation_time**|`datetime2(4)`<br /><br /> `not null`|8 octets|Heure actuelle.|Date et heure de création du fichier.|Calculé automatiquement. Peut également être défini à l'aide d'API Windows.|  
|**last_write_time**|`datetime2(4)`<br /><br /> `not null`|8 octets|Heure actuelle.|Date et heure de dernière mise à jour du fichier.|Calculé automatiquement. Peut également être défini à l'aide d'API Windows.|  
|**last_access_time**|`datetime2(4)`<br /><br /> `not null`|8 octets|Heure actuelle.|Date et heure du dernier accès au fichier.|Calculé automatiquement. Peut également être défini à l'aide d'API Windows.|  
|**is_directory**|`bit`<br /><br /> `not null`|1 octet|FALSE|Indique si la ligne représente un répertoire. Cette valeur est calculée automatiquement et ne peut pas être définie.|Calculé automatiquement. Ne peut pas être définie.|  
|**is_offline**|`bit`<br /><br /> `not null`|1 octet|FALSE|Attribut de fichier hors connexion.|Calculé automatiquement. Peut également être défini à l'aide d'API Windows.|  
|**is_hidden**|`bit`<br /><br /> `not null`|1 octet|FALSE|Attribut de fichier masqué.|Calculé automatiquement. Peut également être défini à l'aide d'API Windows.|  
|**is_readonly**|`bit`<br /><br /> `not null`|1 octet|FALSE|Attribut de fichier en lecture seule.|Calculé automatiquement. Peut également être défini à l'aide d'API Windows.|  
|**is_archive**|`bit`<br /><br /> `not null`|1 octet|FALSE|Attribut Archive.|Calculé automatiquement. Peut également être défini à l'aide d'API Windows.|  
|**is_system**|`bit`<br /><br /> `not null`|1 octet|FALSE|Attribut de fichier système.|Calculé automatiquement. Peut également être défini à l'aide d'API Windows.|  
|**is_temporary**|`bit`<br /><br /> `not null`|1 octet|FALSE|Attribut de fichier temporaire.|Calculé automatiquement. Peut également être défini à l'aide d'API Windows.|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer, modifier et supprimer des FileTables](create-alter-and-drop-filetables.md)  
  
  