---
title: sp_bindsession (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_bindsession
- sp_bindsession_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_bindsession
ms.assetid: 1436fe21-ad00-4a98-aca1-1451a5e571d2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a24c219937341b7c1f9d44515bf52c4de220d4c2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47851987"
---
# <a name="spbindsession-transact-sql"></a>sp_bindsession (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Lie ou la dissociation d’une session à d’autres sessions dans la même instance de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. La liaison de sessions permet à deux sessions ou plus de participer à la même transaction et d'en partager les verrous jusqu'à l'émission d'une instruction ROLLBACK TRANSACTION ou COMMIT TRANSACTION.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez plutôt MARS (Multiple Active Results Sets) ou des transactions distribuées. Pour plus d’informations, consultez [Utilisation de MARS &#40;Multiple Active Result Sets&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_bindsession { 'bind_token' | NULL }  
```  
  
## <a name="arguments"></a>Arguments  
 **«** *bind_token* **»**  
 Est le jeton qui identifie la transaction obtenu à l’origine à l’aide de **sp_getbindtoken** ou Open Data Services **srv_getbindtoken** (fonction). *bind_token*est **varchar (255)**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 Deux sessions liées ne partage qu'une transaction et des verrous. Chaque session conserve son propre niveau d'isolation et la définition d'un nouveau niveau d'isolation sur une session n'affecte pas le niveau de l'autre. Chaque session reste identifiée par son compte de sécurité et ne peut accéder qu'aux ressources de la base de données auxquelles le compte est autorisé à accéder.  
  
 **sp_bindsession** utilise un jeton de liaison pour lier deux ou plusieurs sessions clientes existantes. Ces sessions clientes doivent se trouver sur la même instance de la [!INCLUDE[ssDE](../../includes/ssde-md.md)] à partir duquel le jeton de liaison a été obtenu. Une session est un client exécutant une commande. Les sessions de base de données liées partagent une transaction et un espace de verrouillage.  
  
 Un jeton de liaison obtenu à partir d’une instance de la [!INCLUDE[ssDE](../../includes/ssde-md.md)] ne peut pas être utilisé pour une session client connectée à une autre instance, même pour les transactions DTC. Un jeton de liaison n'est valide que localement dans chaque instance et ne peut pas être partagé par plusieurs instances. Pour lier des sessions clientes sur une autre instance de la [!INCLUDE[ssDE](../../includes/ssde-md.md)], vous devez obtenir un jeton de liaison différent en exécutant **sp_getbindtoken**.  
  
 **sp_bindsession** échoue avec une erreur si elle utilise un jeton qui n’est pas actif.  
  
 Détacher une session à l’aide **sp_bindsession** sans spécifier *bind_token* ou en passant la valeur NULL dans *bind_token*.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant associe le jeton de liaison spécifié à la session active.  
  
> [!NOTE]  
>  Le jeton de liaison indiqué dans l’exemple a été obtenu en exécutant **sp_getbindtoken** avant d’exécuter **sp_bindsession**.  
  
```  
USE master;  
GO  
EXEC sp_bindsession 'BP9---5---->KB?-V'<>1E:H-7U-]ANZ';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_getbindtoken &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql.md)   
 [srv_getbindtoken &#40;API de procédure stockée étendue&#41;](../../relational-databases/extended-stored-procedures-reference/srv-getbindtoken-extended-stored-procedure-api.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
