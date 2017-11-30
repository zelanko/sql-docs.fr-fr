---
title: sp_cursorclose (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_cursor_close_TSQL
- sp_cursor_close
dev_langs: TSQL
helpviewer_keywords: sp_cursorclose
ms.assetid: d9b7b44d-cdff-456e-97df-7031a3b9beb6
caps.latest.revision: "7"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 957036828022476a837a95a4ea4262d1b5312873
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="spcursorclose-transact-sql"></a>sp_cursorclose (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ferme et annule le curseur, mais aussi libère toutes les ressources associées ; Autrement dit, elle supprime la table temporaire utilisée pour prendre en charge le jeu de clés ou statiques **curseur**. sp_cursorclose est appelée en spécifiant ID = 9 dans un paquet de stream (TDS) de données tabulaires.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_cursorclose cursor  
```  
  
## <a name="arguments"></a>Arguments  
 *cursor*  
 Est un curseur *gérer* valeur générée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et retournée par la procédure sp_cursoropen. *curseur* est un paramètre obligatoire qui demande un **int** valeur d’entrée.  
  
> [!NOTE]  
>  La valeur d'entrée -1 s'appliquera vers tous les curseurs de la connexion actuelle.  
  
## <a name="remarks"></a>Notes  
 *curseur* renvoie des messages d’erreur si la procédure a été exécutée une fois que le curseur a été fermé ou si un handle non valide est spécifié.  
  
 L'état RPC indique le succès ou l'échec global.  
  
 Le nombre de lignes DONE est toujours égal à 0.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_cursoropen &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
