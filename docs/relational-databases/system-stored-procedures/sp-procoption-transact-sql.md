---
title: sp_procoption (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_procoption
- sp_procoption_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_procoption
ms.assetid: 6f0221bd-70b4-4b04-b15d-722235aceb3c
author: stevestein
ms.author: sstein
ms.openlocfilehash: bc004c611c218324ce2d2d8b764b3ab05cb73e5d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67896596"
---
# <a name="sp_procoption-transact-sql"></a>sp_procoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Définit ou désactive l'exécution automatique d'une procédure stockée. Une procédure stockée qui a la valeur exécution automatique s’exécute chaque fois qu' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] une instance de est démarrée.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_procoption [ @ProcName = ] 'procedure'   
    , [ @OptionName = ] 'option'   
    , [ @OptionValue = ] 'value'   
```  
  
## <a name="arguments"></a>Arguments  
`[ @ProcName = ] 'procedure'`Nom de la procédure pour laquelle définir une option. la *procédure* est **nvarchar (776)**, sans valeur par défaut.  
  
`[ @OptionName = ] 'option'`Nom de l’option à définir. La seule valeur pour l' *option* est **Startup**.  
  
`[ @OptionValue = ] 'value'`Indique s’il faut définir l’option sur (**true** ou **on**) ou sur OFF (**false** ou **off**). la *valeur* est de type **varchar (12)**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (succès) ou numéro d'erreur (échec)  
  
## <a name="remarks"></a>Notes  
 Les procédures de démarrage doivent se trouver dans la base de données **Master** et ne peuvent pas contenir de paramètres d’entrée ou de sortie. L'exécution des procédures stockées démarre lorsque toutes les bases de données sont récupérées et le message « Récupération terminée » est enregistré au démarrage.  
  
## <a name="permissions"></a>Autorisations  
 Requiert l’appartenance au rôle serveur fixe **sysadmin** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant définit une procédure en vue d'une exécution automatique.  
  
```  
EXEC sp_procoption @ProcName = N'<procedure name>'   
    , @OptionName = 'startup'   
    , @OptionValue = 'on';   
```  
  
 L'exemple suivant empêche une procédure de s'exécuter automatiquement.  
  
```  
EXEC sp_procoption @ProcName = N'<procedure name>'      
    , @OptionName = 'startup'
    , @OptionValue = 'off';   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exécuter une procédure stockée](../../relational-databases/stored-procedures/execute-a-stored-procedure.md)  
  
  
