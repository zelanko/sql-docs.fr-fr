---
title: Pile des appels, fenêtre | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Call Stack Window [Transact-SQL]
ms.assetid: ddb0b19c-87cd-4883-bcb8-ec09ffb30369
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cb1838890edb044ca3f1bbe5dfd5ebd3dad51c9d
ms.sourcegitcommit: 40c3b86793d91531a919f598dd312f7e572171ec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53328689"
---
# <a name="call-stack-window"></a>Fenêtre Pile des appels
  La fenêtre **Pile des appels** affiche les modules de la pile des appels, ainsi que les types de données et les valeurs des paramètres transmis aux modules. [!INCLUDE[tsql](../../includes/tsql-md.md)] Les modules incluent des déclencheurs, des fonctions et des procédures stockées. Pour afficher la pile des appels, vous devez être en mode débogage.  
  
## <a name="task-list"></a>Liste des tâches  
 **Pour accéder à la fenêtre Pile des appels**  
  
-   Dans le menu **Déboguer** , cliquez sur **Fenêtres**, puis sur **Pile des appels**.  
  
 **Pour modifier le frame de pile des appels actuel**  
  
 Vous pouvez utiliser l'une des procédures suivantes pour faire d'un frame de pile le frame actuel :  
  
-   Cliquez avec le bouton droit sur le frame de pile, puis cliquez sur **Basculer vers le frame**.  
  
-   Double-cliquez sur le frame de pile.  
  
 **Pour afficher la source d'un frame autre que le frame actuel**  
  
-   Cliquez avec le bouton droit sur le frame de pile, puis cliquez sur **Atteindre le code source**.  
  
## <a name="stack-frames"></a>Frames de pile  
 Chaque ligne figurant dans la fenêtre **Pile des appels[!INCLUDE[tsql](../../includes/tsql-md.md)] s’appelle un frame de pile et représente soit un appel d’un fichier de script**  à un module, soit un appel d’un module à un autre. Le frame de pile qui figure au bas de l’écran représente la ligne de la fenêtre de l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui a effectué le premier appel dans la pile. La ligne du haut représente la ligne dans laquelle le débogueur a suspendu l’exécution ; elle est identifiée par une flèche jaune dans la marge de gauche de la fenêtre. Chaque ligne intermédiaire indique le module et le numéro de ligne du code source qui a appelé le frame de pile situé immédiatement au-dessus.  
  
 Toutes les expressions figurant dans les fenêtres **Variables locales**, **Espion**et **Espion express** sont évaluées en fonction du frame de pile actuel. La fenêtre de l'éditeur de requête affiche le code pour le frame actuel. Par défaut, le frame de pile actuel est le frame dans lequel le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] a suspendu l’exécution. Quand vous passez du frame de pile actuel à un autre frame, les expressions contenues dans les fenêtres **Variables locales**, **Espion**et **Espion express** sont réévaluées dans le contexte du nouveau frame, et le code source du nouveau frame est affiché dans la fenêtre de l’éditeur de requête.  
  
## <a name="columns"></a>Colonnes  
 **Nom**  
 Affiche les informations relatives à un module de la pile des appels.  
  
 Pour la ligne inférieure de la pile des appels, **Nom** répertorie la fenêtre source de l’éditeur de requête et le numéro de ligne du premier appel de la pile. Pour les autres lignes, **Nom** présente le format **Module(Instance.Database)(ParmList) LineNumber**.  
  
 **Module**  
 Nom de la procédure stockée ou de la fonction qui a appelé le frame suivant.  
  
 **Instance.Database**  
 Instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et base de données qui détiennent le module.  
  
 **ParmList**  
 Indique le type de données, le nom et la valeur de chaque paramètre transmis lors de l'appel au module.  
  
 **LineNumber**  
 Pour toutes les lignes à l’exception de la ligne du haut, **LineNumber** indique la ligne du module qui a appelé le frame. Pour la ligne du haut, **LineNumber** indique la ligne que le débogueur est en train de traiter.  
  
 **Langage**  
 Affiche **Transact-SQL** pour [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Débogueur Transact-SQL](transact-sql-debugger.md)   
 [Informations du débogueur Transact-SQL](transact-sql-debugger-information.md)   
 [Exécuter pas à pas du code Transact-SQL](step-through-transact-sql-code.md)  
