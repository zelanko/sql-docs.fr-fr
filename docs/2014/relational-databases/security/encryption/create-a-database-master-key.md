---
title: Créer une clé principale de base de données | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2019
ms.prod: sql-server-2014
ms.reviewer: carlrab
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], creating
ms.assetid: 8cb24263-e97d-4e4d-9429-6cf494a4d5eb
author: jaszymas
ms.author: jaszymas
manager: craigg
ms.openlocfilehash: 86f74710e99079d0acd28db09bcf1e4ba7c57865
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74957243"
---
# <a name="create-a-database-master-key"></a>Créer une clé principale de base de données

Cette rubrique explique comment créer une clé principale de base de données `master` dans la [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] base de [!INCLUDE[tsql](../../../includes/tsql-md.md)]données dans à l’aide de.

**Dans cette rubrique**

- **Avant de commencer :**

  [Sécurité](#Security)

- [Pour créer une clé principale de base de données à l’aide de Transact-SQL](#TsqlProcedure)

## <a name="BeforeYouBegin"></a> Avant de commencer

### <a name="Security"></a> Sécurité

#### <a name="Permissions"></a> Autorisations

Requiert l'autorisation CONTROL sur la base de données.

## <a name="TsqlProcedure"></a> Utilisation de Transact-SQL

### <a name="to-create-a-database-master-key"></a>Pour créer une clé principale de base de données

1. Choisissez un mot de passe pour chiffrer la copie de la clé principale qui sera stockée dans la base de données.
2. Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../../includes/ssde-md.md)].
3. Développez **Bases de données système**, cliquez avec le bouton droit sur `master`, puis cliquez sur **Nouvelle requête**.
4. Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.

  ```sql
  -- Creates the master key.
  -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe."
  CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';
```

Pour plus d’informations, consultez [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql).
