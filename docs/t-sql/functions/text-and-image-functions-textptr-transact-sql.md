---
title: TEXTPTR (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 10/23/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TEXTPTR_TSQL
- TEXTPTR
dev_langs: TSQL
helpviewer_keywords:
- TEXTPTR function
- viewing text pointer values
- text-pointer values
- displaying text pointer values
ms.assetid: 2672b8cb-f747-46f3-9358-9b49b3583b8e
caps.latest.revision: "36"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 109f9bdd06bf27928450c89ad06dc6d93247b881
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="text-and-image-functions---textptr-transact-sql"></a>Fonctions texte et Image - TEXTPTR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le pointeur de texte la valeur qui correspond à un **texte**, **ntext**, ou **image** colonne **varbinary** format. La valeur du pointeur de texte obtenue peut être utilisée dans les instructions READTEXT, WRITETEXT et UPDATETEXT.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Aucune fonctionnalité de remplacement n'est disponible.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
TEXTPTR ( column )  
```  
  
## <a name="arguments"></a>Arguments  
 *colonne*  
 Est la **texte**, **ntext**, ou **image** colonne qui sera utilisé.  
  
## <a name="return-types"></a>Types de retour  
 **varbinary**  
  
## <a name="remarks"></a>Notes  
 Pour les tables avec du texte en ligne, TEXTPTR renvoie un descripteur pour le texte à traiter. Vous pouvez obtenir un pointeur de texte valide même lorsque la valeur du texte est nulle.  
  
 Vous ne pouvez pas utiliser la fonction TEXTPTR sur des colonnes de vues. Vous ne pouvez l'utiliser que sur des colonnes de tables. Pour utiliser la fonction TEXTPTR sur une colonne d’une vue, vous devez définir le niveau de compatibilité 80, à l’aide de [niveau de compatibilité ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md). Si la table ne possède pas de texte dans la ligne et si un **texte**, **ntext**, ou **image** colonne n’a pas été initialisée par une instruction UPDATETEXT, TEXTPTR renvoie un pointeur null.  
  
 Utilisez TEXTVALID pour vérifier l'existence d'un pointeur de texte. Vous ne pouvez pas utiliser UPDATETEXT, WRITETEXT ou READTEXT sans pointeur de texte valide.  
  
 Les fonctions et les instructions suivantes sont également utiles lorsque vous travaillez avec **texte**, **ntext**, et **image** données.  
  
|Fonction ou instruction| Description|  
|---------------------------|-----------------|  
|La fonction PATINDEX**(«***modèle %***»,** *expression***)**|Retourne la position de caractère d’une chaîne de caractères spécifié dans **texte** ou **ntext** colonnes.|  
|DATALENGTH**(***expression***)**|Retourne la longueur des données dans **texte**, **ntext**, et **image** colonnes.|  
|SET TEXTSIZE|Retourne la limite, en octets, de la **texte**, **ntext**, ou **image** données à retourner avec une instruction SELECT.|  
|SOUS-chaîne**(***colonne_texte*, *Démarrer*, *longueur***)**|Retourne un **varchar** chaîne spécifiée par le *Démarrer* offset et *longueur*. La longueur doit être inférieure à 8 Ko.|  
  
## <a name="examples"></a>Exemples  
  
> [!NOTE]  
>  Pour exécuter les exemples suivants, vous devez installer le **pubs** base de données.  
  
### <a name="a-using-textptr"></a>A. Utilisation de TEXTPTR  
 L’exemple suivant utilise le `TEXTPTR` afin de localiser le **image** colonne `logo` associés `New Moon Books` dans le `pub_info` table de la `pubs` base de données. Le pointeur de texte identifie la variable locale `@ptrval.`.  
  
```  
USE pubs;  
GO  
DECLARE @ptrval varbinary(16);  
SELECT @ptrval = TEXTPTR(logo)  
FROM pub_info pr, publishers p  
WHERE p.pub_id = pr.pub_id   
   AND p.pub_name = 'New Moon Books';  
GO  
```  
  
### <a name="b-using-textptr-with-in-row-text"></a>B. Utilisation de TEXTPTR avec du texte dans la ligne  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le pointeur de texte dans la ligne doit être utilisé au sein d'une transaction, comme le montre l'exemple suivant.  
  
```  
CREATE TABLE t1 (c1 int, c2 text);  
EXEC sp_tableoption 't1', 'text in row', 'on';  
INSERT t1 VALUES ('1', 'This is text.');  
GO  
BEGIN TRAN;  
   DECLARE @ptrval VARBINARY(16);  
   SELECT @ptrval = TEXTPTR(c2)  
   FROM t1  
   WHERE c1 = 1;  
   READTEXT t1.c2 @ptrval 0 1;  
COMMIT;  
```  
  
### <a name="c-returning-text-data"></a>C. Renvoi des données texte  
 Cet exemple sélectionne la colonne `pub_id` et le pointeur de texte sur 16 octets de la colonne `pr_info` dans la table `pub_info`.  
  
```  
USE pubs;  
GO  
SELECT pub_id, TEXTPTR(pr_info)  
FROM pub_info  
ORDER BY pub_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pub_id                                      
------ ----------------------------------   
0736   0x6c0000000000feffb801000001000100   
0877   0x6d0000000000feffb801000001000300   
1389   0x6e0000000000feffb801000001000500   
1622   0x700000000000feffb801000001000900   
1756   0x710000000000feffb801000001000b00   
9901   0x720000000000feffb801000001000d00   
9952   0x6f0000000000feffb801000001000700   
9999   0x730000000000feffb801000001000f00   
  
(8 row(s) affected)  
```  
  
 Cet exemple indique comment retourner les `8000` premiers octets de texte sans utiliser TEXTPTR.  
  
```  
USE pubs;  
GO  
SET TEXTSIZE 8000;  
SELECT pub_id, pr_info  
FROM pub_info  
ORDER BY pub_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pub_id pr_info                                                                                                                                                                                                                                                           
------ -----------------------------------------------------------------  
0736   New Moon Books (NMB) has just released another top ten publication. With the latest publication this makes NMB the hottest new publisher of the year!                                                                                                             
0877   This is sample text data for Binnet & Hardley, publisher 0877 in the pubs database. Binnet & Hardley is located in Washington, D.C.  
  
This is sample text data for Binnet & Hardley, publisher 0877 in the pubs database. Binnet & Hardley is located in Washi   
1389   This is sample text data for Algodata Infosystems, publisher 1389 in the pubs database. Algodata Infosystems is located in Berkeley, California.  
  
9999   This is sample text data for Lucerne Publishing, publisher 9999 in the pubs database. Lucerne publishing is located in Paris, France.  
  
This is sample text data for Lucerne Publishing, publisher 9999 in the pubs database. Lucerne publishing is located in   
  
(8 row(s) affected)  
```  
  
### <a name="d-returning-specific-text-data"></a>D. Renvoi des données texte spécifiques  
 L’exemple suivant recherche le `text` colonne (`pr_info`) associé `pub_id``0736` dans les `pub_info` table de la `pubs` base de données. Elle commence par déclarer la variable locale `@val`. Le pointeur de texte (une chaîne binaire de type long) est ensuite placé dans `@val`, puis passé comme paramètre à l'instruction `READTEXT`. Cette opération renvoie 10 octets à partir du cinquième octet (décalage de 4 octets).  
  
```  
USE pubs;  
GO  
DECLARE @val varbinary(16);  
SELECT @val = TEXTPTR(pr_info)   
FROM pub_info  
WHERE pub_id = '0736';  
READTEXT pub_info.pr_info @val 4 10;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pr_info                                                                                                                                                                                                                                                           
-----------------------------------------------------------------------  
 is sample  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DATALENGTH &#40; Transact-SQL &#41;](../../t-sql/functions/datalength-transact-sql.md)   
 [La fonction PATINDEX &#40; Transact-SQL &#41;](../../t-sql/functions/patindex-transact-sql.md)   
 [READTEXT &#40; Transact-SQL &#41;](../../t-sql/queries/readtext-transact-sql.md)   
 [SET TEXTSIZE &#40; Transact-SQL &#41;](../../t-sql/statements/set-textsize-transact-sql.md)   
 [Texte et Image fonctions &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)   
 [UPDATETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/updatetext-transact-sql.md)   
 [WRITETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/writetext-transact-sql.md)  
  
  
