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
manager: craigg
ms.openlocfilehash: aee8c496db092787720ea8f778697b5a7b3fdd22
ms.sourcegitcommit: e9fcd10c7eb87a4f09ac2d8f7647018e83a5f5c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57973918"
---
# <a name="spprocoption-transact-sql"></a>sp_procoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Définit ou désactive l'exécution automatique d'une procédure stockée. Une procédure stockée qui est la valeur d’exécution automatique s’exécute chaque fois qu’une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est démarré.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_procoption [ @ProcName = ] 'procedure'   
    , [ @OptionName = ] 'option'   
    , [ @OptionValue = ] 'value'   
```  
  
## <a name="arguments"></a>Arguments  
 [  **@ProcName =** ] **'**_procédure_**'**  
 Est le nom de la procédure pour laquelle définir une option. *procédure* est **nvarchar(776)**, sans valeur par défaut.  
  
 [ **@OptionName =** ] **'**_option_**'**  
 Nom de l'option que vous voulez paramétrer. La seule valeur pour *option* est **démarrage**.  
  
 [  **@OptionValue =** ] **'**_valeur_**'**  
 Indique si l’option sur (**true** ou **sur**) ou désactivé (**false** ou **hors**). *valeur* est **varchar(12)**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (succès) ou numéro d'erreur (échec)  
  
## <a name="remarks"></a>Notes  
 Procédures de démarrage doivent se trouver dans le **master** de base de données et ne peut pas contenir de paramètres d’entrée ou de sortie. L'exécution des procédures stockées démarre lorsque toutes les bases de données sont récupérées et le message « Récupération terminée » est enregistré au démarrage.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle serveur fixe **sysadmin** .  
  
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
  
  
