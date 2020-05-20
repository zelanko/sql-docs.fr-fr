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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 26f298a102c69c8bc75721db531275379080005a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830969"
---
# <a name="sp_prepexecrpc-transact-sql"></a>sp_prepexecrpc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Prépare et exécute un appel de procédure stockée paramétrable spécifié à l'aide d'un identificateur RPC. sp_prepexecrpc est appelée par ID = 14 dans un paquet tabular data stream (TDS).  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_prepexecrpc handle OUTPUT, RPCCall  
    [ , bound_param ] [ ,...n]]  
```  
  
## <a name="arguments"></a>Arguments  
 *traitée*  
 Identificateur de handle préparé généré par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *handle* est un paramètre obligatoire avec une valeur de retour **int** .  
  
 *RPCCall*  
 Définit l'appel de procédure stockée à l'aide de la syntaxe canonique ODBC. *RPCCall* est un paramètre obligatoire qui appelle une valeur d’entrée de chaîne **ntext** .  
  
 *bound_param*  
 Indique l'utilisation facultative de paramètres supplémentaires. *bound_param* appelle une valeur d’entrée de n’importe quel type de données pour désigner les paramètres supplémentaires en cours d’utilisation.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
