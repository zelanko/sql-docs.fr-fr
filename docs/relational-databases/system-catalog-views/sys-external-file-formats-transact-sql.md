---
title: Sys.external_file_formats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a89efb2c-0a3a-4b64-9284-6e93263e29ac
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b16deb7ed2bd43cc45966d27b79729897e76405c
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52532359"
---
# <a name="sysexternalfileformats-transact-sql"></a>Sys.external_file_formats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Contient une ligne pour chaque format de fichier externe dans la base de données actuelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)], et [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
 Contient une ligne pour chaque format de fichier externe sur le serveur pour [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|file_format_id|**Int**|ID d’objet pour le format de fichier externe.||  
|NAME|**sysname**|Nom du format de fichier. dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], il est unique pour la base de données. Dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], il est unique pour le serveur.||  
|format_type|**tinyint**|Le type de format de fichier.|DELIMITEDTEXT, RCFILE, ORC, PARQUET|  
|indicateur_fin_de_champ|**nvarchar(10)**|Pour format_type = DELIMITEDTEXT, c’est la marque de fin de champ.||  
|string_delimiter|**nvarchar(10)**|Pour format_type = DELIMITEDTEXT, il s’agit du délimiteur de chaîne.||  
|date_format|**nvarchar(50)**|Pour format_type = DELIMITEDTEXT, c’est la date défini par l’utilisateur et le format d’heure.||  
|use_type_default|**bit**|Pour format_type = texte délimité par des, spécifie comment gérer les valeurs manquantes lorsque PolyBase est l’importation de données à partir de fichiers texte HDFS [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].|0 - stocker des valeurs manquantes en tant que la chaîne « NULL ».<br /><br /> 1 - stocker des valeurs manquantes en tant que la valeur par défaut de la colonne.|  
|serde_method|**nvarchar(255)**|Pour format_type = RCFILE, c’est la méthode de sérialisation/désérialisation.||  
|indicateur_fin_de_ligne|**nvarchar(10)**|Pour format_type = DELIMITEDTEXT, c’est la chaîne de caractère qui arrête chaque ligne dans le fichier Hadoop externe.|Toujours '\n'.|  
|encodage|**nvarchar(10)**|Pour format_type = DELIMITEDTEXT, c’est la méthode d’encodage du fichier Hadoop externe.|Toujours 'UTF8'.|  
|data_compression|**nvarchar(255)**|La méthode de compression de données pour les données externes.|Pour format_type = DELIMITEDTEXT :<br /><br /> -   'org.apache.hadoop.io.compress.DefaultCodec'<br />-   'org.apache.hadoop.io.compress.GzipCodec'<br /><br /> Pour format_type = RCFILE :<br /><br /> -   'org.apache.hadoop.io.compress.DefaultCodec'<br /><br /> Pour format_type = ORC :<br /><br /> -   'org.apache.hadoop.io.compress.DefaultCodec'<br />-   'org.apache.hadoop.io.compress.SnappyCodec'<br /><br /> Pour format_type = PARQUET :<br /><br /> -   'org.apache.hadoop.io.compress.GzipCodec'<br />-   'org.apache.hadoop.io.compress.SnappyCodec'|  
  
## <a name="permissions"></a>Autorisations  
 La visibilité des métadonnées dans les affichages catalogue est limitée aux éléments sécurisables qu'un utilisateur détient ou pour lesquels des autorisations lui ont été accordées. Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [sys.external_data_sources &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)   
 [sys.external_tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-tables-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)  
  
  
