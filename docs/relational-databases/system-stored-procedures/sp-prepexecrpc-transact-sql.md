---
title: sp_prepexecrpc (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepexecrpc
- sp_cursor_prepexecrpc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepexecrpc
ms.assetid: 35d686f2-ef31-4eaa-baa9-9cef5d6c87c2
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6d17320174703e8fc6b21d7fecb83229f80bac41
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="spprepexecrpc-transact-sql"></a>sp_prepexecrpc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Prépare et exécute un appel de procédure stockée paramétrable spécifié à l'aide d'un identificateur RPC. sp_prepexecrpc est appelée par ID = 14 dans un paquet de stream (TDS) de données tabulaires.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_prepexecrpc handle OUTPUT, RPCCall  
    [ , bound_param ] [ ,...n]]  
```  
  
## <a name="arguments"></a>Arguments  
 *handle*  
 Identificateur de handle préparé généré par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *gérer les* est un paramètre obligatoire avec une **int** valeur de retour.  
  
 *RPCCall*  
 Définit l'appel de procédure stockée à l'aide de la syntaxe canonique ODBC. *RPCCall* est un paramètre obligatoire qui demande un **ntext** valeur d’entrée de chaîne.  
  
 *bound_param*  
 Indique l'utilisation facultative de paramètres supplémentaires. *bound_param* appelle une valeur d’entrée de tout type de données pour désigner les paramètres supplémentaires en cours d’utilisation.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
