---
title: Fenêtre Commande
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a7f8e72831e333323621279a0403e95e6a134860
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718412"
---
# <a name="command-window"></a>Fenêtre Commande
  Utilisez la **Fenêtre Commande** pour exécuter des commandes, telles que les commandes de débogage et de modification, sur le code contenu dans la fenêtre de l’éditeur de requête du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] en cours de débogage. Vous devez être en mode débogage pour pouvoir utiliser la **Fenêtre Commande**. Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] prend en charge la plupart des commandes qui sont également prises en charge dans la fenêtre [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Command** window. Pour plus d’informations, consultez [Fenêtre Commande de Visual Studio](https://go.microsoft.com/fwlink/?LinkId=112007).  
  
## <a name="task-list"></a>Liste des tâches  
 **Pour accéder à la Fenêtre Commande**  
  
-   Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**.  
  
 **Pour imprimer la valeur d'une variable**  
  
-   Dans la **fenêtre Commande**, tapez **Debug.Print \<nom_variable>** , puis appuyez sur Entrée.  
  
 **Pour afficher des informations sur le thread actuel**  
  
-   Dans **CommandWindow**, tapez `Debug.ListThread` , puis appuyez sur entrée.  
  
 **Pour ajouter une variable à la fenêtre Espion express**  
  
-   Dans la **fenêtre Commande**, tapez **Debug.QuickWatch \<nom_variable>** , puis appuyez sur Entrée.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogueur Transact-SQL](transact-sql-debugger.md)  
