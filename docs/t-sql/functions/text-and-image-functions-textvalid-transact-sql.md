---
title: TEXTVALID (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TEXTVALID_TSQL
- TEXTVALID
dev_langs:
- TSQL
helpviewer_keywords:
- invalid text pointers [SQL Server]
- valid text pointers [SQL Server]
- TEXTVALID function
- checking text pointers
- text-pointer values
- verifying text pointers
ms.assetid: 9411c349-b59b-4740-a270-92f91d81ad23
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 279022316af7e3a396c7089f48933281264f900f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="text-and-image-functions---textvalid-transact-sql"></a>Fonctions texte et Image - TEXTVALID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  A **texte**, **ntext**, ou **image** fonction qui vérifie si un pointeur de texte spécifique est valide.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Aucune fonctionnalité de remplacement n'est disponible.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
TEXTVALID ( 'table.column' ,text_ ptr )  
```  
  
## <a name="arguments"></a>Arguments  
 *table*  
 Nom de la table à utiliser.  
  
 *colonne*  
 Nom de la colonne à utiliser.  
  
 *pointeur_texte*  
 Pointeur texte à vérifier.  
  
## <a name="return-types"></a>Types de retour  
 **int**  
  
## <a name="remarks"></a>Notes  
 Retourne 1 si le pointeur est valide et 0 si le pointeur n'est pas valide. Notez que l’identificateur de la **texte** colonne doit inclure le nom de la table. Vous ne pouvez pas utiliser UPDATETEXT, WRITETEXT ou READTEXT sans pointeur de texte valide.  
  
 Les instructions et les fonctions suivantes sont également utiles lorsque vous travaillez avec **texte**, **ntext**, et **image** données.  
  
|Fonction ou instruction| Description|  
|---------------------------|-----------------|  
|La fonction PATINDEX**(**'*modèle %**'***,** *expression***)**|Retourne la position de caractère d’une chaîne de caractères spécifié dans **texte** et **ntext** colonnes.|  
|DATALENGTH**(***expression***)**|Retourne la longueur des données dans **texte**, **ntext**, et **image** colonnes.|  
|SET TEXTSIZE|Retourne la limite, en octets, de la **texte**, **ntext**, ou **image** données à retourner avec une instruction SELECT.|  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant indique si un pointeur de texte valide existe pour chaque valeur dans la colonne `logo` de la table `pub_info`.  
  
> [!NOTE]  
>  Pour exécuter cet exemple, vous devez installer le **pubs** base de données.  
  
```  
USE pubs;  
GO  
SELECT pub_id, 'Valid (if 1) Text data'   
   = TEXTVALID ('pub_info.logo', TEXTPTR(logo))   
FROM pub_info  
ORDER BY pub_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pub_id Valid (if 1) Text data   
------ ----------------------   
0736   1                        
0877   1                        
1389   1                        
1622   1                        
1756   1                        
9901   1                        
9952   1                        
9999   1                        
  
(8 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DATALENGTH &#40; Transact-SQL &#41;](../../t-sql/functions/datalength-transact-sql.md)   
 [La fonction PATINDEX &#40; Transact-SQL &#41;](../../t-sql/functions/patindex-transact-sql.md)   
 [SET TEXTSIZE &#40; Transact-SQL &#41;](../../t-sql/statements/set-textsize-transact-sql.md)   
 [Texte et Image fonctions &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)   
 [TEXTPTR &#40; Transact-SQL &#41;](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)  
  
  

