---
description: APP_NAME (Transact-SQL)
title: APP_NAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- APP_NAME_TSQL
- APP_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- name checking for current session [SQL Server]
- sessions [SQL Server], application names
- applications [SQL Server], names
- current session application names
- APP_NAME function
ms.assetid: e491e192-9b30-4243-bc19-33c133fe08a8
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c8522004e6852ebb3e874811ec7eb198cdf0416a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88417515"
---
# <a name="app_name-transact-sql"></a>APP_NAME (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Cette fonction retourne le nom de l’application pour la session active, si l’application définit la valeur de ce nom.
  
> [!IMPORTANT]  
>  Le client fournit le nom de l’application, et `APP_NAME` ne vérifie la valeur de ce nom en aucune façon. N'utilisez pas `APP_NAME` dans le cadre d'une vérification de sécurité.  
  
![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
  
APP_NAME  ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Types de retour
**nvarchar(128)**
  
## <a name="remarks"></a>Remarques  
Utilisez `APP_NAME` pour faire la distinction entre différentes applications, comme un moyen d’effectuer des actions différentes pour ces applications. Par exemple, `APP_NAME` peut faire la distinction entre les différentes applications, ce qui autorise un format de date différent pour chaque application. Elle peut également autoriser le renvoi d’un message d’information à certaines applications.
  
Pour définir un nom d’application dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], cliquez sur **Options** dans la boîte de dialogue **Se connecter au moteur de base de données**. Sous l’onglet **Paramètres de connexion supplémentaires**, spécifiez un attribut **app** au format `;app='application_name'`
  
## <a name="example"></a>Exemple  
Cet exemple vérifie si l’application cliente qui a lancé ce traitement est une session `SQL Server Management Studio`. Il fournit ensuite une valeur de date au format US ou ANSI.
  
```sql
USE AdventureWorks2012;  
GO  
IF APP_NAME() = 'Microsoft SQL Server Management Studio - Query'  
PRINT 'This process was started by ' + APP_NAME() + '. The date is ' + CONVERT ( varchar(100) , GETDATE(), 101) + '.';  
ELSE   
PRINT 'This process was started by ' + APP_NAME() + '. The date is ' + CONVERT ( varchar(100) , GETDATE(), 102) + '.';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi
[Fonctions système &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-category-transact-sql.md)  
[Fonctions](../../t-sql/functions/functions.md)
  
  
