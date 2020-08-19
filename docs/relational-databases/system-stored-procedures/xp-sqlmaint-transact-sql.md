---
description: xp_sqlmaint (Transact-SQL)
title: xp_sqlmaint (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_sqlmaint
- xp_sqlmaint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_sqlmaint
ms.assetid: bda66e1b-6bbd-49be-b86e-37efc920e912
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cfe66be84a9f631422c624eaf65152569d0405bd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419183"
---
# <a name="xp_sqlmaint-transact-sql"></a>xp_sqlmaint (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Appelle l’utilitaire **sqlmaint** avec une chaîne qui contient des commutateurs **sqlmaint**. L’utilitaire **sqlmaint** effectue un ensemble d’opérations de maintenance sur une ou plusieurs bases de données.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
xp_sqlmaint 'switch_string'     
```  
  
## <a name="arguments"></a>Arguments  
 **'** *switch_string* **'**  
 Chaîne contenant les commutateurs de l’utilitaire **sqlmaint** . Les commutateurs et leurs valeurs doivent être séparés par un espace.  
  
 Le **- ?** le commutateur n’est pas valide pour **xp_sqlmaint**.  
  
## <a name="return-code-values"></a>Codet de retour  
 Aucun. Retourne une erreur si l’utilitaire **sqlmaint** échoue.  
  
## <a name="remarks"></a>Notes  
 Si cette procédure est appelée par un utilisateur connecté avec SQL Server l’authentification, les commutateurs **-U «***login_id***»** et **-P «***mot de passe***** » sont ajoutés à *switch_string* avant l’exécution. Si l’utilisateur a ouvert une session avec l’authentification Windows, *switch_string* est passé sans modification à **sqlmaint**.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle serveur fixe **sysadmin** .  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, `xp_sqlmaint` appelle `sqlmaint` pour réaliser des contrôles d'intégrité, créer un fichier de rapport et mettre à jour `msdb.dbo.sysdbmaintplan_history`.  
  
```  
EXEC xp_sqlmaint '-D AdventureWorks2012 -PlanID 02A52657-D546-11D1-9D8A-00A0C9054212   
   -Rpt "C:\Program Files\Microsoft SQL Server\MSSQL\LOG\DBMaintPlan2.txt" -WriteHistory  -CkDB -CkAl';   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
The command(s) executed successfully.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire sqlmaint](../../tools/sqlmaint-utility.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
