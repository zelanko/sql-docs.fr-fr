---
title: Mettre à l’échelle l’exécution simultanée de scripts externes
description: Configurez l’exécution de scripts R et Python parallèles ou simultanés dans un pool de comptes d’utilisateur pour mettre à l’échelle SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a5a0cd5ab05f7675ce011fe5205cbba3432725f4
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715865"
---
# <a name="scale-concurrent-execution-of-external-scripts-in-sql-server-machine-learning-services"></a>Mettre à l’échelle l’exécution simultanée de scripts externes dans SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans le cadre du processus d’installation de [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)], un *pool de comptes d’utilisateurs* Windows est créé pour prendre en charge l’exécution de tâches par le service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]. L’objectif de ces comptes de travail est d’isoler l’exécution simultanée de scripts externes par différents utilisateurs SQL.

Cet article décrit la configuration et la capacité par défaut des comptes de travail, ainsi que la façon de modifier la configuration par défaut pour mettre à l’échelle le nombre d’exécutions simultanées de scripts externes dans SQL Server Machine Learning Services.

## <a name="worker-account-group"></a>Groupe de comptes Worker

Un groupe de comptes Windows est créé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le programme d’installation de pour chaque instance sur laquelle machine learning est installé et activé.

- Dans une instance par défaut, le nom du groupe est **SQLRUserGroup**. Le nom est le même que vous utilisiez R ou python ou les deux.
- Dans une instance nommée, le nom du groupe par défaut a pour suffixe le nom de l’instance (par exemple, **SQLRUserGroupMyInstanceName**).

Par défaut, le pool de comptes d’utilisateurs contient 20 comptes d’utilisateurs. Dans la plupart des cas, 20 est plus que suffisant pour prendre en charge les tâches de Machine Learning, mais vous pouvez modifier le nombre de comptes. Le nombre maximal de comptes est de 100.

- Dans une instance par défaut, les comptes individuels sont nommés **MSSQLSERVER01** à **MSSQLSERVER20**.
- Pour une instance nommée, les comptes individuels sont nommés en fonction du nom de l’instance (par exemple, **MyInstanceName01** à **MyInstanceName20**).

Si plusieurs instances utilisent Machine Learning, l’ordinateur aura plusieurs groupes d’utilisateurs. Un groupe ne peut pas être partagé entre plusieurs instances.

> [!Note]
> Dans SQL Server 2019, **SQLRUserGroup** ne possède qu’un seul membre qui est maintenant le seul compte de service SQL Server Launchpad au lieu de plusieurs comptes Worker.

<a name = "HowToChangeGroup"> </a>

## <a name="number-of-worker-accounts"></a>Nombre de comptes de travail

Pour modifier le nombre d’utilisateurs dans le pool de comptes, vous devez modifier les propriétés du service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], comme décrit ci-dessous.

Les mots de passe associés à chaque compte d’utilisateur sont générés de manière aléatoire, mais vous pouvez les modifier une fois les comptes créés.

1. Ouvrez le Gestionnaire de configuration SQL Server, puis sélectionnez **SQL Server Services**.
2. Double-cliquez sur le service SQL Server Launchpad et arrêtez-le s’il est en cours d’exécution.
3.  Sous l’onglet **Service**, vérifiez que le mode de démarrage Automatique est sélectionné. Les scripts externes ne peuvent pas démarrer lorsque le Launchpad n’est pas en cours d’exécution.
4.  Cliquez sur l’onglet **Avancé** et, si nécessaire, modifiez le **Nombre d’utilisateurs externes**. Ce paramètre contrôle le nombre d’utilisateurs SQL différents qui peuvent exécuter simultanément des sessions de script externes. La valeur par défaut est 20 comptes. Le nombre maximal d’utilisateurs est de 100.
5. Vous pouvez éventuellement affecter à l’option **Réinitialiser le mot de passe des utilisateurs externes** la valeur _Oui_ si une stratégie exigeant le changement périodique des mots de passe est en place dans votre organisation. Cette opération regénère les mots de passe chiffrés que gère Launchpad pour les comptes d’utilisateurs. Pour plus d’informations, consultez [Appliquer la stratégie des mots de passe](../security/sql-server-launchpad-service-account.md#bkmk_EnforcePolicy).
6.  Redémarrez le service launchpad.

## <a name="managing-workloads"></a>Gestion des charges de travail

Le nombre de comptes dans ce pool détermine le nombre de sessions de script externes pouvant être actives simultanément.  Par défaut, 20 comptes sont créés, ce qui signifie que 20 utilisateurs différents peuvent avoir des sessions R ou python actives en même temps. Vous pouvez augmenter le nombre de comptes de travail, si vous prévoyez d’exécuter plus de 20 scripts simultanés.

Quand un même utilisateur exécute plusieurs scripts externes simultanément, toutes les sessions exécutées par cet utilisateur utilisent le même compte de travail. Par exemple, un seul utilisateur peut avoir 100 différents scripts R s’exécutant simultanément, tant que les ressources le permettent, mais tous les scripts s’exécutent à l’aide d’un seul compte de travail.

Le nombre de comptes de travail que vous pouvez prendre en charge, ainsi que le nombre de sessions simultanées qu’un utilisateur unique peut exécuter, est limité uniquement par les ressources du serveur. En général, la mémoire est le premier goulot d’étranglement que vous rencontrez quand vous utilisez le runtime R.

Les ressources qui peuvent être utilisées par les scripts Python ou R sont régies par SQL Server. Nous vous recommandons de surveiller l’utilisation des ressources à l’aide de vues de gestion dynamique de SQL Server, ou d’examiner les compteurs de performances sur l’objet de traitement Windows associé, puis d’ajuster l’utilisation de la mémoire du serveur en conséquence. Si vous avez SQL Server Entreprise édition, vous pouvez allouer des ressources utilisées pour l’exécution de scripts externes en configurant un [pool de ressources externes](how-to-create-a-resource-pool.md).

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur la configuration de la capacité, consultez les articles suivants:

- [Configuration de SQL Server pour R services](../../advanced-analytics/r/sql-server-configuration-r-services.md)
- [Étude de cas sur les performances pour R services](../../advanced-analytics/r/performance-case-study-r-services.md)