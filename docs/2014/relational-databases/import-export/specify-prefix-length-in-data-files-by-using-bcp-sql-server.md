---
title: Spécifier une longueur de préfixe dans des fichiers de données à l’aide de bcp (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server], prefix length
- prefix length [SQL Server]
- lengths [SQL Server], prefix characters
- data formats [SQL Server], prefix length
ms.assetid: ce32dd1a-26f1-4f61-b9fa-3f1feea9992e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b1f480c361c465f17fa50d2a13df29f44a56d131
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48058759"
---
# <a name="specify-prefix-length-in-data-files-by-using-bcp-sql-server"></a>Spécifier une longueur de préfixe dans des fichiers de données à l'aide de bcp (SQL Server)
  Pour un stockage de fichier plus compact lors de l’exportation en bloc de données au format natif vers un fichier de données, la commande **bcp** ajoute devant chaque champ un ou plusieurs caractères indiquant la longueur du champ. Ces caractères portent le nom de *caractères de préfixe de longueur*.  
  
## <a name="the-bcp-prompt-for-prefix-length"></a>Demande de longueur de préfixe par la commande bcp  
 Si une commande **bcp** interactive contient l’option **in** ou **out** sans commutateur de fichier de format (**-f**) ou sans commutateur de format de données (**-n**, **-c**, **-w**ou **-N**), la commande demande la longueur de préfixe de chaque champ de données, comme suit :  
  
 `Enter prefix length of field <field_name> [<default>]:`  
  
 Si vous spécifiez 0, **bcp** vous invite à fournir la longueur du champ (pour un type de données caractère) ou une terminaison de champ (pour un type de données natif non caractère).  
  
> [!NOTE]  
>  Après avoir indiqué de façon interactive tous les champs d’une commande **bcp**, cette dernière vous demande de sauvegarder vos réponses dans un fichier de format autre que XML pour chacun des champs fournis. Pour plus d’informations sur les fichiers de format non-XML, consultez [Fichiers de format non-XML &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
## <a name="overview-of-prefix-length"></a>Présentation de la longueur de préfixe  
 Pour stocker la longueur de préfixe d'un champ, vous avez besoin d'un nombre suffisant d'octets pour représenter la longueur maximale du champ. Le nombre d'octets requis dépend également du type de stockage de fichier, de la possibilité de valeurs Null d'une colonne et de ce que les données sont stockées dans le fichier de données au format natif ou au format caractère. Par exemple, un `text` ou `image` type de données requiert quatre caractères de préfixe pour stocker la longueur de champ, mais un `varchar` type de données requiert deux caractères. Dans le fichier de données, ces caractères sont stockés au format de données binaire interne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Lorsque vous utilisez le format natif, préférez les préfixes de longueur aux indicateurs de fin de champ. Les données au format natif peuvent entrer en conflit avec les indicateurs de fin, car ces fichiers sont au format de données binaire interne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
##  <a name="PrefixLengthsExport"></a> Longueurs de préfixe pour l'exportation en bloc  
  
> [!NOTE]  
>  La valeur par défaut fournie lors de la demande de longueur de préfixe lorsque vous exportez un champ indique la longueur de champ la plus efficace pour le champ.  
  
 Les valeurs NULL sont représentées comme un champ vide. Pour indiquer que le champ est vide (représente NULL), le préfixe de champ contient la valeur -1, signifiant qu'il nécessite au moins 1 octet. Notez que si une colonne de table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autorise les valeurs NULL, la colonne requiert une longueur de préfixe de 1 ou plus, selon le type de stockage du fichier.  
  
 Lorsque vous exportez des données en bloc et que vous les stockez dans un format avec des types de données natifs ou au format caractère, utilisez les longueurs de préfixe répertoriées dans le tableau suivant.  
  
|SQL Server<br /><br /> type de données|Format natif<br /><br /> NOT NULL|Format natif<br /><br /> NULL|Format caractère<br /><br /> NOT NULL|Format caractère<br /><br /> NULL|  
|------------------------------|--------------------------------|----------------------------|-----------------------------------|-------------------------------|  
|`char`|2|2|2|2|  
|`varchar`|2|2|2|2|  
|`nchar`|2|2|2|2|  
|`nvarchar`|2|2|2|2|  
|`text` <sup>1</sup>|4|4|4|4|  
|`ntext` <sup>1</sup>|4|4|4|4|  
|`binary`|2|2|2|2|  
|`varbinary`|2|2|2|2|  
|`image` <sup>1</sup>|4|4|4|4|  
|`datetime`|0|1|0|1|  
|`smalldatetime`|0|1|0|1|  
|`decimal`|1|1|1|1|  
|`numeric`|1|1|1|1|  
|`float`|0|1|0|1|  
|`real`|0|1|0|1|  
|`int`|0|1|0|1|  
|`bigint`|0|1|0|1|  
|`smallint`|0|1|0|1|  
|`tinyint`|0|1|0|1|  
|`money`|0|1|0|1|  
|`smallmoney`|0|1|0|1|  
|`bit`|0|1|0|1|  
|`uniqueidentifier`|1|1|0|1|  
|`timestamp`|1|1|1|1|  
|`varchar(max)`|8|8|8|8|  
|`varbinary(max)`|8|8|8|8|  
|UDT (type de données défini par l'utilisateur)|8|8|8|8|  
|XML|8|8|8|8|  
  
 <sup>1</sup> le `ntext`, `text`, et `image` types de données seront supprimées dans une future version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Évitez d'utiliser ces types de données dans un nouveau développement. Prévoyez de modifier les applications qui les utilisent actuellement. Utilisez `nvarchar(max)`, `varchar(max)`, et `varbinary(max)` à la place.  
  
##  <a name="PrefixLengthsImport"></a> Longueurs de préfixe pour l'importation en bloc  
 Lorsque vous importez des données en bloc, la longueur de préfixe correspond à la valeur spécifiée lors de la création du fichier de données. Si le fichier de données n’a pas été créé à l’aide d’une commande **bcp** , il n’existe probablement pas de caractères de longueur de préfixe. Dans ce cas, vous devez préciser la valeur 0 comme longueur de préfixe.  
  
> [!NOTE]  
>  Pour spécifier une longueur de préfixe dans un fichier de données qui n’a pas été créé à l’aide de **bcp**, utilisez les longueurs indiquées dans [Longueurs de préfixe pour l’exportation en bloc](#PrefixLengthsExport), plus haut dans cette rubrique.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire bcp](../../tools/bcp-utility.md)   
 [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Spécifier la longueur des champs au moyen de bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md)   
 [Spécifier des indicateurs de fin de champ et de fin de ligne &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)   
 [Spécifier le type de stockage de fichiers à l’aide de bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
  
