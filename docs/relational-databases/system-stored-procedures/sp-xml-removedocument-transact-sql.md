---
title: sp_xml_removedocument (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_xml_removedocument_TSQL
- sp_xml_removedocument
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xml_removedocument
ms.assetid: f9dca50a-8baf-4170-90bc-e72783ce5b73
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ed76914663049816d7877e6fe4e3ad3709d2f3b4
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43027090"
---
# <a name="spxmlremovedocument-transact-sql"></a>sp_xml_removedocument (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime la représentation interne du document XML spécifié par le descripteur du document puis invalide le descripteur.  
  
> [!NOTE]  
>  Un document analysé est stocké dans le cache interne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'analyseur MSXML (Msxmlsql.dll) utilise un huitième de la mémoire totale disponible pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour éviter de manquer de mémoire, exécutez **sp_xml_removedocument** pour libérer de la mémoire.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_xml_removedocument hdoc  
```  
  
## <a name="arguments"></a>Arguments  
 *hdoc*  
 Descripteur du document nouvellement créé. Un descripteur incorrect renvoie une erreur. *hdoc* est un entier.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou >0 (échec)  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 Le code exemple suivant supprime la représentation interne d'un document XML. Le descripteur du document est fourni en entrée.  
  
```  
EXEC sp_xml_removedocument @hdoc;  
```  
  
## <a name="see-also"></a>Voir aussi      
 <br>[Procédures système (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)
 <br>[XML procédures stockées (Transact-SQL)](../../relational-databases/system-stored-procedures/xml-stored-procedures-transact-sql.md)
 <br>[Sys.dm_exec_xml_handles (Transact-SQL)](../system-dynamic-management-views/sys-dm-exec-xml-handles-transact-sql.md)
 <br>[sp_xml_preparedocument(Transact-SQL)](../../relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql.md)
 <br>[OPENXML (Transact-SQL)](../../t-sql/functions/openxml-transact-sql.md)
  
  
