---
title: Fenêtre Commande
titleSuffix: T-SQL debugger
ms.prod: sql
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 12/04/2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 226acc4696b5edacde3b6950c10c8b5370e29b42
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75243431"
---
# <a name="transact-sql-debugger---command-window"></a>Débogueur Transact-SQL - Fenêtre Commande

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Utilisez la **Fenêtre Commande** pour exécuter des commandes, telles que les commandes de débogage et de modification, sur le code contenu dans la fenêtre de l’éditeur de requête du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] en cours de débogage. Vous devez être en mode débogage pour pouvoir utiliser la **Fenêtre Commande**. Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] prend en charge la plupart des commandes qui sont également prises en charge dans la fenêtre [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Command** window. Pour plus d’informations, consultez [Fenêtre Commande de Visual Studio](https://go.microsoft.com/fwlink/?LinkId=112007).  

[!INCLUDE[ssms-old-versions](../../includes/ssms-old-versions.md)]

## <a name="task-list"></a>Liste des tâches

**Pour accéder à la Fenêtre Commande**

- Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**.

**Pour imprimer la valeur d'une variable**

- Dans la **fenêtre Commande**, tapez **Debug.Print \<nom_variable>** , puis appuyez sur Entrée.

**Pour afficher des informations sur le thread actuel**

- Dans la **Fenêtre Commande**, tapez **Debug.ListThread**et appuyez sur Entrée.

**Pour ajouter une variable à la fenêtre Espion express**

- Dans la **fenêtre Commande**, tapez **Debug.QuickWatch \<nom_variable>** , puis appuyez sur Entrée.

## <a name="see-also"></a>Voir aussi

[Débogueur Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)
