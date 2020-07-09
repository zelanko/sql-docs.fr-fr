---
title: -- (Comment) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/25/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- --_TSQL
- Comment
- --
dev_langs:
- TSQL
helpviewer_keywords:
- nonexecuting text strings [SQL Server]
- remarks [SQL Server]
- -- (comment character)
- comments [SQL Server]
ms.assetid: 676ea8c2-52c1-4ef6-9354-320f1a091153
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d8432437ffab7f0b98593015f42aaa9c9bdaa366
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86005035"
---
# <a name="---comment-transact-sql"></a>'-- (Comment) (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Indique un texte défini par l'utilisateur. Il est possible d'insérer des commentaires sur une ligne distincte, imbriqués à la fin d'une ligne de commande [!INCLUDE[tsql](../../includes/tsql-md.md)] ou à l'intérieur d'une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)]. Le serveur n'évalue pas ces commentaires.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
-- text_of_comment  
```  
  
## <a name="arguments"></a>Arguments  
 *text_of_comment*  
 Chaîne de caractères contenant le texte du commentaire.  
  
## <a name="remarks"></a>Notes  
Utilisez deux tirets ( **--** ) pour un commentaire d’une seule ligne ou imbriqué. Les commentaires insérés avec **--** se terminent par une nouvelle ligne, qui est spécifiée par un caractère de retour chariot (U+000A), un caractère de saut de ligne (U+000D) ou une combinaison des deux. Il n'y a pas de longueur maximale pour les commentaires. Le tableau suivant répertorie les raccourcis clavier que vous pouvez utiliser pour commenter du texte ou annuler les marques de commentaire de ce dernier.
  
|Action|standard|  
|------------|--------------|  
|Mettre le texte sélectionné en commentaire|Ctrl+K, Ctrl+C|  
|Ne pas commenter le texte sélectionné|Ctrl+K, Ctrl+U|  
  
 Pour plus d’informations sur les raccourcis clavier, consultez [Raccourcis clavier dans SQL Server Management Studio](../../ssms/sql-server-management-studio-keyboard-shortcuts.md).  
  
 Pour les commentaires multilignes, consultez [Barre oblique étoile &#40;bloc de commentaire&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/slash-star-comment-transact-sql.md).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise les caractères d'indication de commentaire --.  
  
```  
-- Choose the AdventureWorks2012 database.  
USE AdventureWorks2012;  
GO  
-- Choose all columns and all rows from the Address table.  
SELECT *  
FROM Person.Address  
ORDER BY PostalCode ASC; -- We do not have to specify ASC because   
-- that is the default.  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Langage de contrôle de flux &#40;Transact-SQL&#41;](~/t-sql/language-elements/control-of-flow.md)  
  
  
