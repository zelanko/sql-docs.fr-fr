---
title: READTEXT (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 10/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- READTEXT_TSQL
- READTEXT
dev_langs:
- TSQL
helpviewer_keywords:
- column reading [SQL Server]
- READTEXT statement
- reading columns
ms.assetid: 91b69853-1381-4306-8343-afdb73105738
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c1659dfcc9ca8908ce756eb41b32fd30649decfa
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="readtext-transact-sql"></a>READTEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Lit **texte**, **ntext**, ou **image** les valeurs d’une **texte**, **ntext**, ou **image** colonne, en commençant à partir d’un offset spécifié et en lisant le nombre spécifié d’octets.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilisez le [sous-chaîne](../../t-sql/functions/substring-transact-sql.md) de fonction à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
READTEXT { table.column text_ptr offset size } [ HOLDLOCK ]  
```  
  
## <a name="arguments"></a>Arguments  
 *table* **.** *column*  
 Nom de la table et de la colonne dont le contenu doit être lu. Les noms de table et de colonne doivent respecter les règles de [identificateurs](../../relational-databases/databases/database-identifiers.md). Les noms de la table et de la colonne sont obligatoires ; ceux de la base de données et du propriétaire sont facultatifs.  
  
 *text_ptr*  
 Pointeur de texte valide. *pointeur_texte* doit être **Binary (16)**.  
  
 *offset*  
 Est le nombre d’octets (lorsque le **texte** ou **image** types de données sont utilisés) ou caractères (lorsque le **ntext** type de données est utilisé) à ignorer avant de commencer à lire le **texte**, **image**, ou **ntext** données.  
  
 *size*  
 Est le nombre d’octets (lorsque le **texte** ou **image** types de données sont utilisés) ou de caractères (lorsque le **ntext** type de données est utilisé) de données à lire. Si *taille* est 0, 4 Ko de données est en lecture.  
  
 HOLDLOCK  
 Demande de verrouiller la valeur texte en lecture jusqu'à la fin de la transaction. Les autres utilisateurs peuvent lire la valeur, mais pas la modifier.  
  
## <a name="remarks"></a>Notes  
 Utilisez le [TEXTPTR](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md) fonction pour obtenir une liste valide *pointeur_texte* valeur. TEXTPTR retourne un pointeur vers le **texte**, **ntext**, ou **image** colonne de la ligne spécifiée ou à la **texte**, **ntext**, ou **image** colonne dans la dernière ligne retournée par la requête si plusieurs lignes sont retournées. Comme la fonction TEXTPTR retourne une chaîne binaire de 16 octets, il est conseillé de déclarer une variable locale pour stocker le pointeur de texte et utiliser cette variable dans READTEXT. Pour plus d’informations sur la déclaration d’une variable locale, consultez [DECLARE @local_variable &#40; Transact-SQL &#41; ](../../t-sql/language-elements/declare-local-variable-transact-sql.md).  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il peut exister des pointeurs de texte dans la ligne non valides. Pour plus d’informations sur la **texte dans la ligne** option, consultez [sp_tableoption &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). Pour plus d’informations sur l’invalidation des pointeurs de texte, consultez [sp_invalidate_textptr &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-invalidate-textptr-transact-sql.md).  
  
 La valeur de la @@TEXTSIZE fonction remplace la taille indiquée dans READTEXT si elle est inférieure à la taille spécifiée pour READTEXT. Le @@TEXTSIZE fonction spécifie la limite du nombre d’octets de données à renvoyer, défini par l’instruction SET TEXTSIZE. Pour plus d’informations sur la façon de définir le paramètre de session, consultez [SET TEXTSIZE &#40; Transact-SQL &#41; ](../../t-sql/statements/set-textsize-transact-sql.md).  
  
## <a name="permissions"></a>Autorisations  
 Les autorisations READTEXT reviennent par défaut aux utilisateurs ayant des autorisations SELECT sur la table indiquée. Ces autorisations peuvent être transférées lorsque les autorisations SELECT sont transférées.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant lit les données du deuxième au vingt-sixième caractères de la colonne `pr_info` de la table `pub_info`.  
  
> [!NOTE]  
>  Pour exécuter cet exemple, vous devez installer le **pubs** base de données exemple.  
  
```  
USE pubs;  
GO  
DECLARE @ptrval varbinary(16);  
SELECT @ptrval = TEXTPTR(pr_info)   
   FROM pub_info pr INNER JOIN publishers p  
      ON pr.pub_id = p.pub_id   
      AND p.pub_name = 'New Moon Books'  
READTEXT pub_info.pr_info @ptrval 1 25;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [@@TEXTSIZE &#40;Transact-SQL&#41;](../../t-sql/functions/textsize-transact-sql.md)   
 [UPDATETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/updatetext-transact-sql.md)   
 [WRITETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/writetext-transact-sql.md)  
  
  
