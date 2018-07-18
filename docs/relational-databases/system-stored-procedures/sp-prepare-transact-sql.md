---
title: sp_prepare (Transact SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepare_TSQL
- sp_cursor_prepare
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepare
ms.assetid: f328c9eb-8211-4863-bafa-347e1bf7bb3f
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 08e1c0f988d480e7c0c98d0818591734574ece87
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036297"
---
# <a name="spprepare-transact-sql"></a>sp_prepare (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Prépare une paramétrable [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction et retourne une instruction *gérer* pour l’exécution. sp_prepare est appelée en spécifiant ID = 11 dans un paquet data stream (TDS).  
  
 ![Icône Lien de l’article](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_prepare handle OUTPUT, params, stmt, options  
```  
  
## <a name="arguments"></a>Arguments  
 *handle*  
 Généré par SQL Server *handle préparé* identificateur. *gérer* est un paramètre obligatoire avec une **int** valeur de retour.  
  
 *params*  
 Identifie des instructions paramétrables. Le *params* définition de variables est substituée aux marqueurs de paramètre dans l’instruction. *params* est un paramètre obligatoire qui demande un **ntext**, **nchar**, ou **nvarchar** valeur d’entrée. Entrez une valeur NULL si l'instruction n'est pas paramétrable.  
  
 *stmt*  
 Définit le jeu de résultats de curseur. Le *stmt* paramètre est obligatoire et demande pour un **ntext**, **nchar**, ou **nvarchar** valeur d’entrée.  
  
 *options*  
 Paramètre optionnel qui retourne une description des colonnes du jeu de résultats du curseur. *options* requiert la valeur d’entrée int suivante :  
  
|Valeur|Description|  
|-----------|-----------------|  
|0x0001|RETURN_METADATA|  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant prépare et exécute une instruction simple.  
  
```  
Declare @P1 int;  
Exec sp_prepare @P1 output,   
    N'@P1 nvarchar(128), @P2 nvarchar(100)',  
    N'SELECT database_id, name FROM sys.databases WHERE name=@P1 AND state_desc = @P2';  
Exec sp_execute @P1, N'tempdb', N'ONLINE';  
EXEC sp_unprepare @P1;  
```  

  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

