---
title: Spécifier le type de stockage de fichiers à l’aide de bcp (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-bulk-import-export
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bcp utility [SQL Server], file storage types
- importing data, file storage types
- native data format [SQL Server]
- file storage types [SQL Server]
- data formats [SQL Server], file storage types
ms.assetid: 85e12df8-1be7-4bdc-aea9-05aade085c06
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 68630ac6e4a2ffad9079ed620e8d7d9660bf6381
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042216"
---
# <a name="specify-file-storage-type-by-using-bcp-sql-server"></a>Spécifier le type de stockage de fichiers à l'aide de bcp (SQL Server)
  Le *type de stockage de fichier* décrit la façon dont les données sont stockées dans le fichier de données. Données peuvent être exportées vers un fichier de données comme type de table de base de données (format natif), dans sa représentation sous forme de caractères (format caractères) ou comme n’importe quel type de données où la conversion implicite est prise en charge ; par exemple, en copiant un `smallint` comme un `int`. Les types de données définis par l'utilisateur sont exportés en tant que leurs propres types de base.  
  
## <a name="the-bcp-prompt-for-file-storage-type"></a>Invite bcp pour le type de stockage de fichier  
 Si une commande **bcp** interactive contient l’option **in** ou **out** sans commutateur de fichier de format (**-f**) ou sans commutateur de format de données (**-n**, **-c**, **-w**ou **-N**), la commande demande le type de stockage de fichiers de chaque champ de données, comme suit :  
  
 `Enter the file storage type of field <field_name> [<default>]:`  
  
 Votre réponse à cette invite dépend de la tâche effectuée :  
  
-   Pour exporter en bloc des données d’une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers un fichier de données au format de stockage le plus compact possible (format de données natif), vous devez accepter les types de stockage de fichier par défaut fournis par l’utilitaire **bcp**. Pour la liste des types de stockage de fichier natifs, consultez la section « Types de stockage de fichier natifs » plus loin dans cette rubrique.  
  
-   Pour exporter des données en bloc à partir d’une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers un fichier de données au format caractère, spécifiez `char` comme type de stockage de fichier pour toutes les colonnes de la table.  
  
-   Pour importer en bloc des données à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d’un fichier de données, spécifiez le type de stockage de fichier en tant que `char` pour les types stockés au caractère de format et, pour les données stockées dans un format de type de données natif, spécifiez un des types de stockage de fichier, comme il convient :  
  
    |type de stockage de fichier|Entrer sur la ligne de commande|  
    |-----------------------|-----------------------------|  
    |`char` <sup>1</sup>|`c`[`har`]|  
    |`varchar`|`c[har]`|  
    |`nchar`|`w`|  
    |`nvarchar`|`w`|  
    |`text` <sup>2</sup>|`T`[`ext`]|  
    |`ntext2`|`W`|  
    |`binary`|`x`|  
    |`varbinary`|`x`|  
    |`image` <sup>2</sup>|`I`[`mage`]|  
    |`datetime`|**d[ate]**|  
    |`smalldatetime`|`D`|  
    |`time`|`te`|  
    |`date`|`de`|  
    |`datetime2`|`d2`|  
    |`datetimeoffset`|`do`|  
    |`decimal`|`n`|  
    |`numeric`|`n`|  
    |`float`|**f[loat]**|  
    |`real`|`r`|  
    |`Int`|**i[nt]**|  
    |`bigint`|`B[igint]`|  
    |`smallint`|**s[mallint]**|  
    |`tinyint`|**t[inyint]**|  
    |`money`|**m[oney]**|  
    |`smallmoney`|`M`|  
    |`bit`|`b[it]`|  
    |`uniqueidentifier`|`u`|  
    |`sql_variant`|`V[ariant]`|  
    |`timestamp`|`x`|  
    |`UDT` (type de données défini par l'utilisateur)|`U`|  
    |`XML`|`X`|  
  
     <sup>1</sup> l’interaction de longueur de champ, la longueur du préfixe et les terminateurs détermine la quantité d’espace de stockage alloué dans un fichier de données pour les données qui sont exportés en tant que le `char` type de stockage de fichier.  
  
     <sup>2</sup> le `ntext`, `text`, et `image` des types de données seront supprimées dans une future version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Dans un nouveau travail de développement, évitez ces types de données et prévoyez la modification des applications qui les utilisent actuellement. Utilisez `nvarchar(max)`, `varchar(max)`, et `varbinary(max)` à la place.  
  
## <a name="native-file-storage-types"></a>Types de stockage de fichier natifs  
 Chaque type de stockage de fichier natif est enregistré dans le fichier de format comme un type de données du fichier hôte correspondant.  
  
|type de stockage de fichier|Type de données du fichier hôte|  
|-----------------------|-------------------------|  
|`char` <sup>1</sup>|SQLCHAR|  
|`varchar`|SQLCHAR|  
|`nchar`|SQLNCHAR|  
|`nvarchar`|SQLNCHAR|  
|`text` <sup>2</sup>|SQLCHAR|  
|`ntext` <sup>2</sup>|SQLNCHAR|  
|`binary`|SQLBINARY|  
|`varbinary`|SQLBINARY|  
|`image` <sup>2</sup>|SQLBINARY|  
|`datetime`|SQLDATETIME|  
|`smalldatetime`|SQLDATETIM4|  
|`decimal`|SQLDECIMAL|  
|`numeric`|SQLNUMERIC|  
|`float`|SQLFLT8|  
|`real`|SQLFLT4|  
|`int`|SQLINT|  
|`bigint`|SQLBIGINT|  
|`smallint`|SQLSMALLINT|  
|`tinyint`|SQLTINYINT|  
|`money`|SQLMONEY|  
|`smallmoney`|SQLMONEY4|  
|`bit`|SQLBIT|  
|`uniqueidentifier`|SQLUNIQUEID|  
|`sql_variant`|SQLVARIANT|  
|`timestamp`|SQLBINARY|  
|UDT (type de données défini par l'utilisateur)|SQLUDT|  
  
 <sup>1</sup> des fichiers de données qui sont stockés dans un caractère de format utilisent `char` en tant que le type de stockage. Par conséquent, pour les fichiers de données de type caractère, SQLCHAR est le seul type de données qui apparaît dans un fichier de format.  
  
 <sup>2</sup> importer des données en bloc `text`, `ntext`, et `image` les colonnes qui ont des valeurs par défaut.  
  
## <a name="additional-considerations-for-file-storage-types"></a>Observations supplémentaires concernant les types de stockage de fichier  
 Lorsque vous exportez des données en bloc à partir d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers un fichier de données :  
  
-   Vous pouvez toujours spécifier `char` comme type de stockage de fichier.  
  
-   Si vous entrez un type de stockage de fichier qui représente une conversion implicite non valide, **bcp** échoue ; par exemple, bien que vous puissiez spécifier `int` pour `smallint` données, si vous spécifiez `smallint` pour `int` des données, erreurs de dépassement se produisent.  
  
-   Lorsque des types de données tels que `float`, `money`, `datetime`, ou `int` sont stockés en tant que leurs types de base de données, les données sont écrites dans le fichier de données dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au format natif.  
  
    > [!NOTE]  
    >  Après avoir indiqué de façon interactive tous les champs d’une commande **bcp**, cette dernière vous demande de sauvegarder vos réponses dans un fichier de format autre que XML pour chacun des champs fournis. Pour plus d’informations sur les fichiers de format non-XML, consultez [Fichiers de format non-XML &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire bcp](../../tools/bcp-utility.md)   
 [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Spécifier la longueur des champs au moyen de bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md)   
 [Spécifier des indicateurs de fin de champ et de fin de ligne &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)   
 [Spécifier une longueur de préfixe dans des fichiers de données à l’aide de bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
  
