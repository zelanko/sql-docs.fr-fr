---
title: Spécifier le type de stockage de fichiers à l’aide de bcp (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server], file storage types
- importing data, file storage types
- native data format [SQL Server]
- file storage types [SQL Server]
- data formats [SQL Server], file storage types
ms.assetid: 85e12df8-1be7-4bdc-aea9-05aade085c06
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c1f3ad2a94ffe3e0f1db19a8e66f85497e7143dc
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85026485"
---
# <a name="specify-file-storage-type-by-using-bcp-sql-server"></a>Spécifier le type de stockage de fichiers à l'aide de bcp (SQL Server)
  Le *type de stockage de fichier* décrit la façon dont les données sont stockées dans le fichier de données. Les données peuvent être exportées vers un fichier de données au type de table de base de données (format natif), dans sa représentation caractères (format caractères) ou tout type de données pour lesquelles la conversion implicite est prise en charge ; par exemple, en copiant un type de données `smallint` comme `int`. Les types de données définis par l'utilisateur sont exportés en tant que leurs propres types de base.  
  
## <a name="the-bcp-prompt-for-file-storage-type"></a>Invite bcp pour le type de stockage de fichier  
 Si une commande **bcp** interactive contient l’option **in** ou **out** sans commutateur de fichier de format ( **-f**) ou sans commutateur de format de données ( **-n**, **-c**, **-w**ou **-N**), la commande demande le type de stockage de fichiers de chaque champ de données, comme suit :  
  
 `Enter the file storage type of field <field_name> [<default>]:`  
  
 Votre réponse à cette invite dépend de la tâche effectuée :  
  
-   Pour exporter des données en bloc d’une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers un fichier de données au format de stockage le plus compact possible (format de données natif), vous devez accepter les types de stockage de fichier par défaut fournis par l’utilitaire **bcp**. Pour la liste des types de stockage de fichier natifs, consultez la section « Types de stockage de fichier natifs » plus loin dans cette rubrique.  
  
-   Pour exporter en bloc des données d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers un fichier de données au format caractère, spécifiez le paramètre `char` comme type de stockage de fichier pour toutes les colonnes de la table.  
  
-   Pour importer en bloc des données dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un fichier de données, spécifiez le type de stockage de fichier `char` pour les types stockés au format caractère et, pour les données stockées dans le format de type de données natif, spécifiez l'un des types de stockage de fichier appropriés :  
  
    |type de stockage de fichier|Entrer sur la ligne de commande|  
    |-----------------------|-----------------------------|  
    |`char`<sup>1</sup>|`c`[`har`]|  
    |`varchar`|`c[har]`|  
    |`nchar`|`w`|  
    |`nvarchar`|`w`|  
    |`text`<sup>2</sup>|`T`[`ext`]|  
    |`ntext2`|`W`|  
    |`binary`|`x`|  
    |`varbinary`|`x`|  
    |`image`<sup>2</sup>|`I`[`mage`]|  
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
  
     <sup>1</sup> l’interaction entre la longueur de champ, la longueur de préfixe et les terminateurs détermine la quantité d’espace de stockage alloué dans un fichier de données pour les données non-caractères exportées en tant que `char` type de stockage de fichier.  
  
     <sup>2</sup> les `ntext` `text` types de données, et `image` seront supprimés dans une future version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Dans un nouveau travail de développement, évitez ces types de données et prévoyez la modification des applications qui les utilisent actuellement. Utilisez `nvarchar(max)` , `varchar(max)` et à la `varbinary(max)` place.  
  
## <a name="native-file-storage-types"></a>Types de stockage de fichier natifs  
 Chaque type de stockage de fichier natif est enregistré dans le fichier de format comme un type de données du fichier hôte correspondant.  
  
|type de stockage de fichier|Type de données du fichier hôte|  
|-----------------------|-------------------------|  
|`char`<sup>1</sup>|SQLCHAR|  
|`varchar`|SQLCHAR|  
|`nchar`|SQLNCHAR|  
|`nvarchar`|SQLNCHAR|  
|`text`<sup>2</sup>|SQLCHAR|  
|`ntext`<sup>2</sup>|SQLNCHAR|  
|`binary`|SQLBINARY|  
|`varbinary`|SQLBINARY|  
|`image`<sup>2</sup>|SQLBINARY|  
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
  
 <sup>1</sup> les fichiers de données qui sont stockés au format caractère utilisent `char` comme type de stockage de fichier. Par conséquent, pour les fichiers de données de type caractère, SQLCHAR est le seul type de données qui apparaît dans un fichier de format.  
  
 <sup>2</sup> vous ne pouvez pas importer des données en bloc dans des `text` `ntext` colonnes, et `image` qui ont des valeurs par défaut.  
  
## <a name="additional-considerations-for-file-storage-types"></a>Observations supplémentaires concernant les types de stockage de fichier  
 Lorsque vous exportez des données en bloc à partir d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers un fichier de données :  
  
-   Vous pouvez toujours spécifier `char` comme type de stockage de fichier.  
  
-   Si vous entrez un type de stockage de fichier qui représente une conversion implicite non valide, **BCP** échoue. par exemple, bien que vous puissiez spécifier `int` pour des `smallint` données, si vous spécifiez `smallint` pour des `int` données, des erreurs de dépassement de capacité se produisent.  
  
-   Lorsque des types de données autres que des caractères tels que `float`, `money`, `datetime` ou `int` sont stockés avec leurs types de base de données, les données sont écrites dans le fichier de données au format natif de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    > [!NOTE]  
    >  Après avoir indiqué de façon interactive tous les champs d’une commande **bcp**, cette dernière vous demande de sauvegarder vos réponses dans un fichier de format autre que XML pour chacun des champs fournis. Pour plus d’informations sur les fichiers de format non-XML, consultez [Fichiers de format non-XML &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire bcp](../../tools/bcp-utility.md)   
 [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Spécifier la longueur des champs au moyen de bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md)   
 [Spécifier des indicateurs de fin de champ et de fin de ligne &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)   
 [Spécifier une longueur de préfixe dans des fichiers de données à l’aide de bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
  
