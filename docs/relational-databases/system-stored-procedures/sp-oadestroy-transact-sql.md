---
title: sp_OADestroy (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_OADestroy_TSQL
- sp_OADestroy
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OADestroy
ms.assetid: 0bd1cff4-ceff-4095-9ae4-e1e65a80f5d6
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 758f9be98c13f599fabcea77d1007c73a688d5e4
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43037376"
---
# <a name="spoadestroy-transact-sql"></a>sp_OADestroy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Détruit un objet OLE créé.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_OADestroy objecttoken      
```  
  
## <a name="arguments"></a>Arguments  
 *objecttoken*  
 Jeton d’objet d’un objet OLE précédemment créé à l’aide de **sp_OACreate**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (succès) ou un nombre différent de zéro (échec), qui représente la valeur entière de HRESULT renvoyée par l'objet OLE Automation.  
  
 Pour plus d’informations sur les Codes de retour HRESULT, consultez [OLE Automation Codes de retour et les informations d’erreur](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="remarks"></a>Notes  
 Si **sp_OADestroy** n’est pas appelée, créé objet OLE est automatiquement détruit à la fin du lot.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle serveur fixe **sysadmin** .  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant détruit l’élément précédemment créé **SQLServer** objet.  
  
```  
EXEC @hr = sp_OADestroy @object;  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées OLE Automation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Exemple de script OLE Automation](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
