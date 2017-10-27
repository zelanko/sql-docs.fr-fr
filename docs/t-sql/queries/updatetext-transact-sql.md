---
title: UPDATETEXT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 10/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UPDATETEXT
- UPDATETEXT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- text updates [SQL Server]
- updating data [SQL Server]
- data updates [SQL Server], UPDATETEXT statement
- UPDATETEXT statement
ms.assetid: d73c28ee-3972-4afd-af8d-ebbbd9e50793
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 49bd324f97f6ba1d2e8a8120bb502199b4ca0f06
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="updatetext-transact-sql"></a>UPDATETEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Des mises à jour existant **texte**, **ntext**, ou **image** champ. Utilisez UPDATETEXT pour modifier uniquement une partie d’un **texte**, **ntext**, ou **image** colonne en place. Utilisez WRITETEXT pour mettre à jour et remplacer dans son ensemble **texte**, **ntext**, ou **image** champ.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilisez les types de données de valeur élevée et la **.** Clause d’écriture de la [mise à jour](../../t-sql/queries/update-transact-sql.md) instruction à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
UPDATETEXT [BULK] { table_name.dest_column_name dest_text_ptr }  
  { NULL | insert_offset }  
     { NULL | delete_length }  
     [ WITH LOG ]  
     [ inserted_data  
    | { table_name.src_column_name src_text_ptr } ]  
```  
  
## <a name="arguments"></a>Arguments  
 BULK  
 Permet aux outils de téléchargement de télécharger un flux de données binaires. Le flux de données doit être fourni par l'outil au niveau du protocole TDS. Lorsque le flux de données n'est pas présent, le processeur de requêtes ignore l'option BULK.  
  
> [!IMPORTANT]  
>  Nous recommandons de ne pas utiliser l'option BULK dans les applications basées sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette option est susceptible d'être modifiée ou supprimée dans une future version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *nom_table* **.** *nom_de_la_colonne_de_destination*  
 Est le nom de la table et **texte**, **ntext**, ou **image** colonne à mettre à jour. Les noms de tables et des noms de colonnes doivent respecter les règles de [identificateurs](../../relational-databases/databases/database-identifiers.md). La spécification des noms de la base de données et du propriétaire est facultative.  
  
 *dest_text_ptr*  
 Est un pointeur de texte valeur (retournée par la fonction TEXTPTR) qui pointe vers le **texte**, **ntext**, ou **image** à jour des données. *dest_text_ptr* doit être **binaire (**16**)**.  
  
 *insert_offset*  
 Position de départ de la mise à jour (commence à zéro). Pour **texte** ou **image** colonnes, *insert_offset* est le nombre d’octets à ignorer depuis le début de la colonne existante avant d’insérer de nouvelles données. Pour **ntext** colonnes, *insert_offset*est le nombre de caractères (chaque **ntext** caractère utilise 2 octets). Existants **texte**, **ntext**, ou **image** données en commençant à cette position sont décalées vers la droite pour libérer de l’espace pour les nouvelles données. Une valeur 0 signifie que les nouvelles données seront insérées au début des données existantes. Une valeur NULL signifie que les nouvelles données seront ajoutées à la fin des données existantes.  
  
 *delete_length*  
 La longueur des données à supprimer des existantes **texte**, **ntext**, ou **image** colonne, en commençant à la *insert_offset* position. Le *delete_length*valeur est spécifiée en octets pour **texte** et **image** colonnes et en caractères pour **ntext** colonnes. Chaque **ntext** caractère utilise 2 octets. La valeur 0 signifie aucune suppression de données. Une valeur NULL supprime toutes les données à partir de la *insert_offset* position à la fin d’existants **texte** ou **image** colonne.  
  
 WITH LOG  
 L'enregistrement dans un journal est déterminé par le mode de récupération en vigueur dans la base de données.  
  
 *inserted_data*  
 Données à insérer dans existants **texte**, **ntext**, ou **image** colonne à la *insert_offset* emplacement. Il s’agit d’un seul **char**, **nchar**, **varchar**, **nvarchar**, **binaire**, **varbinary**, **texte**, **ntext**, ou **image** valeur. *inserted_data* peut être un littéral ou une variable.  
  
 *table_name.src_column_name*  
 Est le nom de la table et **texte**, **ntext**, ou **image** colonne utilisée comme source des données insérées. Les noms de tables et de colonnes doivent respecter les règles des identificateurs.  
  
 *pointeur_du_texte_source*  
 Est un pointeur de texte valeur (retournée par la fonction TEXTPTR) qui pointe vers un **texte**, **ntext**, ou **image** colonne utilisée comme source des données insérées.  
  
> [!NOTE]  
>  *scr_text_ptr* valeur ne doit pas être le même que *dest_text_ptr*valeur.  
  
## <a name="remarks"></a>Notes  
 Les nouvelles données insérées peuvent être une seule *inserted_data* constante, nom de la table, nom de la colonne ou pointeur de texte.  
  
|Action de mise à jour|Paramètres UPDATETEXT|  
|-------------------|---------------------------|  
|Remplacement des données existantes|Spécifiez une valeur non null *insert_offset* valeur, une autre que zéro *delete_length* valeur et les nouvelles données à insérer.|  
|Suppression des données existantes|Spécifiez une valeur non null *insert_offset* une différente de zéro et de valeur *delete_length*. Ne spécifiez pas de nouvelles données à insérer.|  
|Insertion de nouvelles données|Spécifiez le *insert_offset* valeur, un *delete_length* de 0 et les nouvelles données à insérer.|  
  
 Pour de meilleures performances, nous recommandons que **texte**, **ntext** et **image** insérées ou mises à jour dans des tailles de segments qui sont des multiples de 8 040 octets de données.  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], pointeurs de texte dans la ligne **texte**, **ntext**, ou **image** données peuvent exister, mais n’est peut-être pas valides. Pour plus d’informations sur l’option text in row, consultez [sp_tableoption &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). Pour plus d’informations sur l’invalidation des pointeurs de texte, consultez [sp_invalidate_textptr &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-invalidate-textptr-transact-sql.md).  
  
 Pour initialiser **texte** à NULL, utilisez WRITETEXT ; UPDATETEXT initialise **texte** colonnes à une chaîne vide.  
  
## <a name="permissions"></a>Permissions  
 Nécessite une autorisation UPDATE sur la table spécifiée.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant place le pointeur de texte dans la variable locale `@ptrval`, puis utilise `UPDATETEXT` pour corriger une faute d'orthographe.  
  
> [!NOTE]  
>  Pour exécuter cet exemple, vous devez installer la base de données pubs.  
  
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
UPDATETEXT pub_info.pr_info @ptrval 88 1 'b';  
GO  
ALTER DATABASE pubs SET RECOVERY FULL;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [READTEXT &#40; Transact-SQL &#41;](../../t-sql/queries/readtext-transact-sql.md)   
 [TEXTPTR &#40; Transact-SQL &#41;](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)   
 [WRITETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/writetext-transact-sql.md)  
  
  

