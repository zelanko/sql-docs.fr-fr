---
title: Fenêtre Points d'arrêt
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Breakpoints Window [Transact-SQL]
ms.assetid: bad88d10-fdd5-4d3d-b5ea-a4f063847485
author: rothja
ms.author: jroth
ms.openlocfilehash: 9a2b488b13eeb4df7754e331960faedef49b9bdf
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063378"
---
# <a name="breakpoints-window"></a>Fenêtre Points d'arrêt
  La fenêtre **Points d’arrêt** répertorie tous les points d’arrêt définis dans l’éditeur de requête actuel du [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Pour gérer les points d’arrêt, utilisez la barre d’outils de la fenêtre **Points d’arrêt** . Les points d'arrêt sont des emplacements dans le code où l'exécution s'interrompt en mode débogage pour que vous puissiez consulter les données de débogage.  
  
## <a name="task-list"></a>Liste des tâches  
 **Pour accéder à la fenêtre Points d'arrêt**  
  
-   Dans le menu **Déboguer** , cliquez sur **Fenêtres**, puis sur **Points d'arrêt**.  
  
## <a name="breakpoints-window-columns"></a>Colonnes de la fenêtre Points d'arrêt  
 Par défaut, la fenêtre **Point d’arrêt** contient les colonnes suivantes.  
  
 **Nom**  
 Affiche le nom du point d'arrêt. Les noms de points d'arrêt sont fournis par le débogueur. Ce nom comprend le nom de la fenêtre de l'éditeur de requête du moteur de base de données qui contient le point d'arrêt, ainsi que le numéro de ligne correspondant au point d'arrêt dans l'éditeur de requête.  
  
 **Condition**  
 Affiche **(aucune condition)** . Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] ne prend pas en charge la définition de conditions de point d'arrêt.  
  
 **Nombre d'accès**  
 Affiche**toujours s’arrêter**.  
  
 Vous pouvez ajouter et supprimer les colonnes suivantes en les sélectionnant dans la liste **Colonnes** .  
  
 **Filter**  
 Affiche **(aucun)** . Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] ne prend pas en charge la définition de filtres de point d'arrêt.  
  
 **Lorsqu'il est atteint**  
 Affiche **Arrêter**.  
  
 **Langage**  
 Affiche **Transact-SQL** pour [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Fonction**  
 Affiche le numéro de la ligne où le point d'arrêt est défini.  
  
 **File**  
 Affiche le nom du fichier source qui contient le point d'arrêt, ainsi que le numéro de la ligne où le point d'arrêt est défini.  
  
 **Adresse**  
 Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] ne prend pas en charge cette fonctionnalité.  
  
 **Processus**  
 Affiche **[SQL]** pour indiquer qu’il s’agit d’un processus du [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Ce libellé est suivi du nom de l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] dans laquelle le code s'exécute.  
  
## <a name="breakpoints-window-toolbar"></a>Barre d'outils de la fenêtre Points d'arrêt  
 Lorsque la fenêtre active de l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] contient des points d’arrêt actifs, la fenêtre **Points d’arrêt** affiche une barre d’outils qui permet de gérer les points d’arrêt.  
  
 **Supprimer**  
 Supprime le point d'arrêt sélectionné.  
  
 **Supprimer tous les points d'arrêt**  
 Supprime tous les points d’arrêt affichés dans la fenêtre **Points d’arrêt** .  
  
 **Désactiver tous les points d'arrêt**  
 Désactive tous les points d'arrêt de sorte qu'ils n'arrêtent plus l'exécution du code ; toutefois, les points d'arrêt subsistent. Lorsque tous les points d’arrêt sont désactivés, ce bouton devient **Activer tous les points d’arrêt**.  
  
 **Activer tous les points d’arrêt**  
 Active tous les points d'arrêt de sorte qu'ils arrêtent l'exécution du code. Lorsque tous les points d’arrêt sont activés, ce bouton devient **Désactiver tous les points d’arrêt**.  
  
 **Atteindre le code source**  
 Place le curseur sur la ligne de l'éditeur de requête qui contient le point d'arrêt sélectionné.  
  
 **Colonnes**  
 Répertorie toutes les colonnes qui peuvent être affichées dans la fenêtre **Points d’arrêt** . Les colonnes qui sont affichées sont indiquées par une case à cocher. Pour ajouter ou supprimer une colonne dans la fenêtre **Points d’arrêt** , sélectionnez la colonne dans la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogueur Transact-SQL](transact-sql-debugger.md)  
