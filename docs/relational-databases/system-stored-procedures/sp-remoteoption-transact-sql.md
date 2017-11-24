---
title: sp_remoteoption (Transact-SQL) | Documents Microsoft
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
- sp_remoteoption_TSQL
- sp_remoteoption
dev_langs: TSQL
helpviewer_keywords: sp_remoteoption
ms.assetid: c9a7309b-eab7-4192-a414-e282581af4e5
caps.latest.revision: "21"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5bea191258773154019cf91063155be54d7cc373
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="spremoteoption-transact-sql"></a>sp_remoteoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche ou modifie les options d'une ouverture de session distante définie sur le serveur local exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]sp_remoteoption ne modifie aucune option et retourne un message d’erreur. Cette procédure existe uniquement pour des raisons de compatibilité descendante.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_remoteoption [ [ @remoteserver = ] 'remoteserver' ]   
     [ , [ @loginame = ] 'loginame' ]   
     [ , [ @remotename = ] 'remotename' ]   
     [ , [ @optname = ] 'optname' ]   
     [ , [ @optvalue = ] 'optvalue' ]  
```  
  
## <a name="remarks"></a>Notes  
 Cette procédure stockée retourne le message d'erreur suivant :  
  
 `The trusted option in remote login mapping is no longer supported.`  
  
## <a name="see-also"></a>Voir aussi  
 [Serveurs liés &#40;moteur de base de données&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md)  
  
  
