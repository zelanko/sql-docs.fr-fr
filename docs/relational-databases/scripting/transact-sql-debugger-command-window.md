---
title: Commande, fenêtre | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology:
- database-engine
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.CommandWindow
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0af7dde66fcbd5d8bb353ef81adafb94192df096
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="transact-sql-debugger---command-window"></a>Débogueur Transact-SQL - Fenêtre Commande
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Utilisez la **Fenêtre Commande** pour exécuter des commandes, telles que les commandes de débogage et de modification, sur le code contenu dans la fenêtre de l’éditeur de requête du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] en cours de débogage. Vous devez être en mode débogage pour pouvoir utiliser la **Fenêtre Commande**. Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] prend en charge la plupart des commandes qui sont également prises en charge dans la fenêtre [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Command** window. Pour plus d’informations, consultez [Fenêtre Commande de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=112007).  
  
## <a name="task-list"></a>Liste des tâches  
 **Pour accéder à la Fenêtre Commande**  
  
-   Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**.  
  
 **Pour imprimer la valeur d'une variable**  
  
-   Dans la **fenêtre Commande**, tapez **Debug.Print \<nom_variable>**, puis appuyez sur Entrée.  
  
 **Pour afficher des informations sur le thread actuel**  
  
-   Dans la **Fenêtre Commande**, tapez **Debug.ListThread**et appuyez sur Entrée.  
  
 **Pour ajouter une variable à la fenêtre Espion express**  
  
-   Dans la **fenêtre Commande**, tapez **Debug.QuickWatch \<nom_variable>**, puis appuyez sur Entrée.  
  
## <a name="see-also"></a> Voir aussi  
 [Débogueur Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)  
  
  
