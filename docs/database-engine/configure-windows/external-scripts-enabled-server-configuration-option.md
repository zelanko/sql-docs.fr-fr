---
title: External scripts enabled (option de configuration de serveur)
description: Découvrez l’option external scripts enabled dans SQL Server. Après avoir activé l’option, vous pouvez exécuter des scripts externes dans les langages pris en charge, tels que R ou Python.
ms.date: 06/30/2020
ms.prod: sql
ms.technology: machine-learning-services
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- external scripts enabled
- external_scripts_enabled_TSQL
helpviewer_keywords:
- external scripts enabled option
ms.assetid: 9d0ce165-8719-4007-9ae8-00f85cab3a0d
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3346d217228bf6ca914b6ae1aa31af0883383908
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88173240"
---
# <a name="external-scripts-enabled-server-configuration-option"></a>External scripts enabled (option de configuration de serveur)
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Utilisez l’option **external scripts enabled** pour activer l’exécution de scripts avec certaines extensions de langage à distance. Cette propriété est désactivée par défaut. Quand **Machine Learning Services** est installé, le programme d’installation peut éventuellement définir cette propriété sur True.

## <a name="remarks"></a>Notes

Vous devez activer l’option de scripts externes activés avant de pouvoir exécuter un script externe à l’aide de la procédure [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) . Utilisez **sp_execute_external_script** pour exécuter des scripts écrits dans un langage pris en charge comme R ou Python. 

+ Pour [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]

    [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] prend en charge le langage R dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], ainsi qu’un ensemble d’outils de station de travail R et de bibliothèques de connectivité.

    Installez la fonction **Services R** pendant l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour permettre l’exécution de scripts R.

+ Pour [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] et versions ultérieures

    [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] prend en charge les langages R et Python.

    Installez la fonctionnalité **Machine Learning Services** pendant l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour permettre l’exécution de scripts externes. Veillez à sélectionner au moins un langage lors de l’installation initiale : R ou Python, ou les deux.

## <a name="additional-requirements"></a>Autres conditions requises

Après l’installation, exécutez le script suivant pour activer les scripts externes :

```sql
sp_configure 'external scripts enabled', 1;
RECONFIGURE WITH OVERRIDE;  
```

Pour plus d’informations, consultez [Installer SQL Server Machine Learning Services (Python et R) sur Windows](../../machine-learning/install/sql-machine-learning-services-windows-install.md) ou [Linux](../../linux/sql-server-linux-setup-machine-learning-docker.md?toc=/sql/machine-learning/toc.json).

## <a name="see-also"></a>Voir aussi

+ [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)
+ [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)
+ [sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)
+ [Documentation SQL Machine Learning](../../machine-learning/index.yml)
