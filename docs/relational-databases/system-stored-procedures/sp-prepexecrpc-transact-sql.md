---
title: sp_prepexecrpc (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepexecrpc
- sp_cursor_prepexecrpc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepexecrpc
ms.assetid: 35d686f2-ef31-4eaa-baa9-9cef5d6c87c2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6fea210183ae67179dcc6f686e25f939cd00713b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056336"
---
# <a name="spprepexecrpc-transact-sql"></a>sp_prepexecrpc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Prépare et exécute un appel de procédure stockée paramétrable spécifié à l'aide d'un identificateur RPC. sp_prepexecrpc est appelée par ID = 14 dans un paquet data stream (TDS).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_prepexecrpc handle OUTPUT, RPCCall  
    [ , bound_param ] [ ,...n]]  
```  
  
## <a name="arguments"></a>Arguments  
 *handle*  
 Identificateur de handle préparé généré par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *gérer* est un paramètre obligatoire avec une **int** valeur de retour.  
  
 *RPCCall*  
 Définit l'appel de procédure stockée à l'aide de la syntaxe canonique ODBC. *RPCCall* est un paramètre obligatoire qui demande un **ntext** valeur d’entrée de chaîne.  
  
 *bound_param*  
 Indique l'utilisation facultative de paramètres supplémentaires. *bound_param* appelle une valeur d’entrée de n’importe quel type de données pour désigner les paramètres supplémentaires en cours d’utilisation.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
