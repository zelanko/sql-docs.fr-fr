---
title: sp_OAStop (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OAStop
- sp_OAStop_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OAStop
ms.assetid: aa9eab66-c4f7-4ec7-9f0d-5d24d16da654
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cce5ea4d449070bd6757ad268be76a2db9ae6ec9
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82834308"
---
# <a name="sp_oastop-transact-sql"></a>sp_OAStop (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Arrête l'environnement d'exécution de la procédure stockée OLE Automation au niveau du serveur.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_OAStop      
```  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (succès) ou un nombre différent de zéro (échec), qui représente la valeur entière de HRESULT renvoyée par l'objet OLE Automation.  
  
 Pour plus d’informations sur les codes de retour HRESULT, consultez [codes de retour OLE Automation et informations sur les erreurs](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="remarks"></a>Notes  
 Un seul environnement d'exécution est partagé par tous les clients utilisant les procédures stockées de OLE Automation. Si un client appelle **sp_OAStop** l’environnement d’exécution partagé sera arrêté pour tous les clients. Après l’arrêt de l’environnement d’exécution, tout appel à **sp_OACreate** redémarre l’environnement d’exécution.  
  
## <a name="permissions"></a>Autorisations  
 Requiert l’appartenance au rôle serveur fixe **sysadmin** ou l’autorisation EXECUTE directement sur cette procédure stockée. `Ole Automation Procedures`la configuration doit être **activée** pour pouvoir utiliser toute procédure système liée à OLE Automation.  
  
## <a name="examples"></a>Exemples  
 Dans cet exemple, l'environnement d'exécution partagé de OLE Automation est arrêté.  
  
```  
EXEC sp_OAStop;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées OLE Automation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Exemple de script OLE Automation](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
