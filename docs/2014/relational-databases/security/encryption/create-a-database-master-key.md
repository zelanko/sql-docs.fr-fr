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
author: aliceku
ms.author: aliceku
manager: craigg
ms.openlocfilehash: 757b6c62d63da2b8f1fa33e5d704d7a2c4fabd38
ms.sourcegitcommit: 5a61854ddcd2c61bb6da30ccad68f0ad90da0c96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70978369"
---
# <a name="create-a-database-master-key"></a>Créer une clé principale de base de données

Cette rubrique explique comment créer une clé principale de base de données `master` dans la [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] base de [!INCLUDE[tsql](../../../includes/tsql-md.md)]données dans à l’aide de.

**Dans cette rubrique**

- **Avant de commencer :**

  [Sécurité](#Security)

- [Pour créer une clé principale de base de données à l'aide de Transact-SQL](#TsqlProcedure)

## <a name="BeforeYouBegin"></a> Avant de commencer

### <a name="Security"></a> Sécurité

#### <a name="Permissions"></a> Autorisations

Requiert l'autorisation CONTROL sur la base de données.

## <a name="TsqlProcedure"></a> Utilisation de Transact-SQL

### <a name="to-create-a-database-master-key"></a>Pour créer une clé principale de base de données

1. Choisissez un mot de passe pour chiffrer la copie de la clé principale qui sera stockée dans la base de données.
2. Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../../includes/ssde-md.md)].
3. Développez **bases de données système**, cliquez `master` avec le bouton droit sur, puis cliquez sur **nouvelle requête**.
4. Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.

  ```sql
  -- Creates the master key.
  -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe."
  CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';
```

Pour plus d’informations, consultez [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql).
