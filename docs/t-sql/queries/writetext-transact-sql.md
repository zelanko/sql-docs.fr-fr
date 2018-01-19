---
title: WRITETEXT (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 10/23/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WRITETEXT_TSQL
- WRITETEXT
dev_langs: TSQL
helpviewer_keywords:
- replacing data
- WRITETEXT statement
- updating data [SQL Server]
- nonlogged updating
- minimally logged updating [SQL Server]
- overwriting data
- data updates [SQL Server], WRITETEXT statement
ms.assetid: 80c252fd-a8b8-4a2e-888a-059081ed4109
caps.latest.revision: "52"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: d8c66e4a785fd1d731bd55730a8439f5e796b01f
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="writetext-transact-sql"></a>WRITETEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Autorise la mise à jour journalisées et interactive d’un objet **texte**, **ntext**, ou **image** colonne. WRITETEXT remplace totalement les données existantes de la colonne qu'elle affecte. WRITETEXT ne peut pas être utilisé sur **texte**, **ntext**, et **image** colonnes des vues.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilisez les types de données de valeur élevée et la **.** Clause d’écriture de la [mise à jour](../../t-sql/queries/update-transact-sql.md) instruction à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
WRITETEXT [BULK]  
  { table.column text_ptr }  
  [ WITH LOG ] { data }  
```  
  
## <a name="arguments"></a>Arguments  
 BULK  
 Permet aux outils de téléchargement de télécharger un flux de données binaires. Le flux de données doit être fourni par l'outil au niveau du protocole TDS. Lorsque le flux de données n'est pas présent, le processeur de requêtes ignore l'option BULK.  
  
> [!IMPORTANT]  
>  Nous recommandons de ne pas utiliser l'option BULK dans les applications basées sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette option est susceptible d'être modifiée ou supprimée dans une future version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *table* **.column**  
 Est le nom de la table et **texte**, **ntext**, ou **image** colonne à mettre à jour. Les noms de table et de colonne doivent respecter les règles de [identificateurs](../../relational-databases/databases/database-identifiers.md). La spécification des noms de la base de données et du propriétaire est facultative.  
  
 *text_ptr*  
 Est une valeur qui stocke le pointeur vers le **texte**, **ntext**, ou **image** données. *pointeur_texte* doit être **Binary (16)**. Pour créer un pointeur de texte, exécutez une [insérer](../../t-sql/statements/insert-transact-sql.md) ou [mise à jour](../../t-sql/queries/update-transact-sql.md) instruction avec des données qui ne sont pas null pour le **texte**, **ntext**, ou **image** colonne.  
  
 WITH LOG  
 Ignoré par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'enregistrement dans un journal est déterminé par le mode de récupération en vigueur dans la base de données.  
  
 *data*  
 Est la **texte**, **ntext** ou **image** pour stocker les données. *données* peut être un littéral ou un paramètre. La longueur maximale de texte qui peut être inséré de manière interactive au moyen de WRITETEXT est d’environ 120 Ko pour **texte**, **ntext**, et **image** données.  
  
## <a name="remarks"></a>Notes  
 Utilisez WRITETEXT pour remplacer **texte**, **ntext**, et **image** UPDATETEXT pour les modifier et les données **texte**, **ntext**, et **image** données. UPDATETEXT est plus souple, car il modifie uniquement une partie d’un **texte**, **ntext**, ou **image** colonne au lieu de l’ensemble de la colonne.  
  
 Pour de meilleures performances, nous recommandons que **texte**, **ntext**, et **image** insérées ou mises à jour dans les tailles de segment qui sont des multiples de 8 040 octets de données.  
  
 Si le mode de récupération de base de données est simple ou journalisé en bloc, **texte**, **ntext**, et **image** les opérations qui utilisent WRITETEXT sont des opérations journalisées lorsque de nouvelles données sont insérées ou ajoutées.  
  
> [!NOTE]  
>  La journalisation minimale n'est pas utilisée lors de la mise à jour de valeurs existantes.  
  
 Pour que l'instruction WRITETEXT fonctionne correctement, la colonne doit déjà contenir un pointeur de texte valide.  
  
 Si la table n’a pas de texte dans la ligne, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] économise de l’espace en n’initialisant ne pas **texte** lorsque des valeurs null explicites ou implicites sont ajoutées dans les colonnes **texte** colonnes avec INSERT et aucun pointeur de texte peuvent être obtenus pour ces valeurs NULL. Pour initialiser **texte** à NULL, utilisez l’instruction de mise à jour. Si la table contient du texte dans ses lignes, vous n'avez pas besoin d'initialiser la colonne text pour les valeurs NULL et vous pouvez toujours obtenir un pointeur de texte.  
  
 La fonction ODBC SQLPutData est plus rapide et utilise moins de mémoire dynamique que WRITETEXT. Cette fonction peut insérer jusqu'à 2 gigaoctets de **texte**, **ntext**, ou **image** données.  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], en pointeurs de texte de ligne **texte**, **ntext**, ou **image** données peuvent exister, mais n’est peut-être pas valides. Pour plus d’informations sur l’option text in row, consultez [sp_tableoption &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). Pour plus d’informations sur l’invalidation des pointeurs de texte, consultez [sp_invalidate_textptr &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-invalidate-textptr-transact-sql.md).  
  
## <a name="permissions"></a>Autorisations  
 Nécessite une autorisation UPDATE sur la table spécifiée. L'autorisation est transférable lorsque l'autorisation UPDATE est transférée.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant place le pointeur de texte dans la variable locale `@ptrval`, puis `WRITETEXT` place la nouvelle chaîne de texte dans la ligne sur laquelle pointe `@ptrval`.  
  
> [!NOTE]  
>  Pour exécuter cet exemple, vous devez installer l'exemple de base de données pubs.  
  
```  
USE pubs;  
GO  
ALTER DATABASE pubs SET RECOVERY SIMPLE;  
GO  
DECLARE @ptrval binary(16);  
SELECT @ptrval = TEXTPTR(pr_info)   
FROM pub_info pr, publishers p  
WHERE p.pub_id = pr.pub_id   
   AND p.pub_name = 'New Moon Books'  
WRITETEXT pub_info.pr_info @ptrval 'New Moon Books (NMB) has just released another top ten publication. With the latest publication this makes NMB the hottest new publisher of the year!';  
GO  
ALTER DATABASE pubs SET RECOVERY SIMPLE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [UPDATETEXT &#40; Transact-SQL &#41;](../../t-sql/queries/updatetext-transact-sql.md)  
  
  
