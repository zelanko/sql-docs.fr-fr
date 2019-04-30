---
title: Spécifier la longueur des champs au moyen de bcp (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- native data format [SQL Server]
- default field lengths
- field length [SQL Server]
- data formats [SQL Server], field length
- bcp utility [SQL Server], field length
ms.assetid: 240f33ca-ef4a-413a-a4de-831885cb505b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f5ed900eae974eb768223d534e6ac43025e9718c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63154876"
---
# <a name="specify-field-length-by-using-bcp-sql-server"></a>Spécifier la longueur des champs au moyen de bcp (SQL Server)
  La longueur de champ indique le nombre maximal de caractères nécessaires pour représenter les données au format caractères. La longueur de champ est déjà connue si les données sont enregistrées au format natif. Par exemple, les données de type `int` occupent 4 octets. Si vous indiquez 0 pour la longueur de préfixe, le **bcp** des invites de commandes vous longueur des champs, les longueurs de champ par défaut et l’impact de la longueur de champ sur le stockage de données dans les fichiers de données qui contiennent des `char` données.  
  
## <a name="the-bcp-prompt-for-field-length"></a>Invite bcp pour la longueur des champs  
 Si une commande **bcp** interactive contient l’option **in** ou **out** sans commutateur de fichier de format (**-f**) ou sans commutateur de format de données (**-n**, **-c**, **-w** ou **-N**), la commande demande la longueur de champ de chaque champ de données, comme suit :  
  
 `Enter length of field <field_name> [<default>]:`  
  
 Pour obtenir un exemple illustrant cette invite en contexte, consultez [Spécifier des formats de données pour la compatibilité lors de l’utilisation de bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).  
  
> [!NOTE]  
>  Après avoir indiqué de façon interactive tous les champs d’une commande **bcp**, cette dernière vous demande de sauvegarder vos réponses dans un fichier de format autre que XML pour chacun des champs fournis. Pour plus d’informations sur les fichiers de format non-XML, consultez [Fichiers de format non-XML &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
 Plusieurs facteurs déterminent si une commande **bcp** vous demande la longueur de champ :  
  
-   Lorsque vous copiez des types de données dont la longueur n’est pas fixe et que vous spécifiez une longueur de préfixe nulle (0), la commande **bcp** demande la longueur de champ.  
  
-   Lors de la conversion de données non caractères en données caractères, la commande **bcp** suggère une longueur de champ par défaut suffisamment importante pour stocker les données.  
  
-   Si le type de stockage de fichier est non caractère, la commande **bcp** ne demande pas de longueur de champ. Les données sont enregistrées au format natif [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="using-default-field-lengths"></a>Utilisation des longueurs de champs par défaut  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande généralement d’accepter les valeurs par défaut de longueur de champ suggérées par la commande **bcp**. Lors de la création d'un fichier de données en mode caractère, l'utilisation de la longueur de champ par défaut garantit que les données ne sont pas tronquées et que des erreurs de dépassement de capacité numérique ne se produiront pas.  
  
 Des problèmes peuvent se produire si vous spécifiez une longueur de champ incorrecte. Par exemple, si cous copiez des données numériques et si vous spécifiez une longueur de champ trop faible pour ces données, l'utilitaire **bcp** affiche un message de dépassement de capacité et ne copie pas les données. En outre, si vous exportez `datetime` données et spécifiez une longueur de champ inférieure à 26 octets pour la chaîne de caractères, le **bcp** utilitaire tronque les données sans message d’erreur.  
  
> [!IMPORTANT]  
>  Lorsque vous utilisez l'option de taille par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'attend à lire une chaîne complète. Dans certains cas, l'utilisation de la longueur de champ par défaut peut entraîner l'erreur « Fin de fichier inattendue ». En règle générale, cette erreur se produit avec le `money` et `datetime` les types de données lors de la seule partie du champ attendu se produit dans le fichier de données ; par exemple, quand un `datetime` valeur *mm*/*jj*  / *yy* est spécifié sans le composant heure et est donc plus courte que la longueur de 24 caractère attendu d’un `datetime` valeur dans `char` format. Pour éviter ce type d'erreur, utilisez des marques de fin de champ ou des champs de données de longueur fixe, ou modifiez la longueur par défaut du champ en spécifiant une autre valeur.  
  
### <a name="default-field-lengths-for-character-file-storage"></a>Longueur par défaut des champs pour le stockage de fichiers au format caractère  
 Le tableau ci-dessous répertorie les longueurs par défaut des champs à enregistrer dans des fichiers de type caractère. Les données pouvant être de type NULL sont de même longueur que les données de type non NULL.  
  
|Type de données|Longueur par défaut (en caractères)|  
|---------------|-----------------------------------|  
|`char`|Longueur définie pour la colonne|  
|`varchar`|Longueur définie pour la colonne|  
|`nchar`|Le double de la longueur définie pour la colonne|  
|`nvarchar`|Le double de la longueur définie pour la colonne|  
|`Text`|0|  
|`ntext`|0|  
|`bit`|1|  
|`binary`|Le double de la longueur définie pour la colonne + 1|  
|`varbinary`|Le double de la longueur définie pour la colonne + 1|  
|`image`|0|  
|`datetime`|24|  
|`smalldatetime`|24|  
|`float`|30|  
|`real`|30|  
|`int`|12|  
|`bigint`|19|  
|`smallint`|7|  
|`tinyint`|5|  
|`money`|30|  
|`smallmoney`|30|  
|`decimal`|41*|  
|`numeric`|41*|  
|`uniqueidentifier`|37|  
|`timestamp`|17|  
|`varchar(max)`|0|  
|`varbinary(max)`|0|  
|`nvarchar(max)`|0|  
|UDT|Longueur de la colonne d'un terme défini par l'utilisateur (UDT)|  
|XML|0|  
  
 \*Pour plus d’informations sur la `decimal` et `numeric` des types de données, consultez [decimal et numeric &#40;Transact-SQL&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql).  
  
> [!NOTE]  
>  Une colonne de type `tinyint` peut posséder des valeurs comprises entre 0 et 255. Le nombre maximal de caractères nécessaires à la représentation de tout nombre compris dans cet intervalle est de trois (représentant les valeurs comprises entre 100 et 255).  
  
### <a name="default-field-lengths-for-native-file-storage"></a>Longueur par défaut des champs pour le stockage de fichiers au format natif  
 Le tableau ci-dessous répertorie les longueurs par défaut des champs à enregistrer dans des fichiers au format natif. Les données pouvant être de type NULL sont de même longueur que les données de type non NULL. Les données de type caractère sont toujours enregistrées au format caractère.  
  
|Type de données|Longueur par défaut (en caractères)|  
|---------------|-----------------------------------|  
|`bit`|1|  
|`binary`|Longueur définie pour la colonne|  
|`varbinary`|Longueur définie pour la colonne|  
|`image`|0|  
|`datetime`|8|  
|`smalldatetime`|4|  
|`float`|8|  
|`real`|4|  
|`int`|4|  
|`bigint`|8|  
|`smallint`|2|  
|`tinyint`|1|  
|`money`|8|  
|`smallmoney`|4|  
|`decimal` <sup>1</sup>|<sup>*</sup>|  
|`numeric` <sup>1</sup>|<sup>*</sup>|  
|`uniqueidentifier`|16|  
|`timestamp`|8|  
  
 <sup>1</sup> pour plus d’informations sur la `decimal` et `numeric` des types de données, consultez [decimal et numeric &#40;Transact-SQL&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql).  
  
 Dans tous les cas précédents, pour créer un fichier de données pour un chargement ultérieur dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et faire en sorte que l'espace de stockage soit minimal, utilisez un préfixe de longueur avec le type de stockage de fichier et la longueur du champ par défaut.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire bcp](../../tools/bcp-utility.md)   
 [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Spécifier des indicateurs de fin de champ et de fin de ligne &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)   
 [Spécifier une longueur de préfixe dans des fichiers de données à l’aide de bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)   
 [Spécifier le type de stockage de fichiers à l’aide de bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)   
 [Conserver les valeurs NULL ou utiliser la valeur par défaut lors de l’importation en bloc &#40;SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
  
