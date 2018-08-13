---
title: AVEC CHANGE_TRACKING_CONTEXT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- WITH_CHANGE_TRACKING_CONTEXT_TSQL
- WITH CHANGE_TRACKING_CONTEXT
dev_langs:
- TSQL
helpviewer_keywords:
- WITH CHANGE_TRACKING_CONTEXT
- change tracking [SQL Server], WITH CHANGE_TRACKING_CONTEXT
ms.assetid: 885e33a1-602a-4b94-8380-a63ac935a683
caps.latest.revision: 15
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: b43802dd6f568d767ef9f0f4569e0d542595bc47
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39557289"
---
# <a name="with-changetrackingcontext-transact-sql"></a>WITH CHANGE_TRACKING_CONTEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Permet de spécifier le contexte d'une modification, tel qu'un ID d'appelant, lorsque les données sont modifiées. Par exemple, lors de l'utilisation du suivi des modifications, une application peut souhaiter distinguer les modifications apportées par l'application elle-même des modifications apportées aux données à l'extérieur de l'application.  

 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
WITH CHANGE_TRACKING_CONTEXT ( context )  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Contexte*  
 Informations contextuelles fournies par l'application appelante et stockées avec les informations de suivi des modifications pour la modification. *contexte* est **varbinary (128)**.  
  
 La valeur peut être une constante ou une variable, mais ne peut pas être NULL.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant définit le contexte de suivi des modifications pour une modification de données.  
  
```  
WITH CHANGE_TRACKING_CONTEXT ( context )  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de suivi des modifications &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-functions-transact-sql.md)   
 [CHANGETABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/changetable-transact-sql.md)   
 [Suivi des modifications de données &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
