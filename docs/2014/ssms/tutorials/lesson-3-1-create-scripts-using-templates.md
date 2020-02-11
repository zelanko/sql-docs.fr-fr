---
title: Créer des scripts au moyen de modèles | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: ed48014c-3fc9-48ff-8c0f-8d1822195f14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8387cdaf85d6fd7750229fda86c8cb3122b61d90
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62913551"
---
# <a name="create-scripts-using-templates"></a>Créer des scripts au moyen de modèles
  Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] fournit un grand nombre de modèles de scripts contenant les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] pour la plupart des tâches courantes. Ces modèles contiennent des paramètres pour les valeurs fournies par les utilisateurs, telles que les noms des tables. À l'aide de ces paramètres, vous pouvez taper un nom une fois puis le copier automatiquement partout où cela est nécessaire dans le script. Vous pouvez écrire vos propres modèles personnalisés pour prendre en compte les scripts que vous écrivez souvent. Vous pouvez également réorganiser l'arborescence des modèles, déplacer des modèles ou créer de nouveaux dossiers pour y stocker des modèles. Au cours de cet exercice, vous allez utiliser un modèle pour créer une base de données en spécifiant un modèle de classement.  
  
## <a name="using-templates"></a>Utilisation de modèles  
  
#### <a name="to-create-a-script-using-a-template"></a>Pour créer un script à l'aide d'un modèle  
  
1.  Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], dans le menu **Affichage** , cliquez sur **Explorateur de modèles**.  
  
2.  Dans l'Explorateur de modèles, les modèles sont organisés par groupe. Développez **Base de données**, puis double-cliquez sur **Créer une base de données**.  
  
3.  Dans la boîte de dialogue **Se connecter au moteur de base de données** , fournissez les informations de connexion, puis cliquez sur **Se connecter**. Une nouvelle fenêtre de l’Éditeur de requête s’affiche et présente le contenu du modèle **Créer une base de données** .  
  
4.  Dans le menu **Requête** , cliquez sur **Spécifier les valeurs des paramètres du modèle**.  
  
5.  Dans la boîte de dialogue **Spécifier les valeurs des paramètres du modèle** , la colonne **Valeur** contient une valeur possible pour le paramètre **Database_Name** . Dans la zone du paramètre **Nom de la base de données** , tapez **Marketing**, puis cliquez sur **OK**. Notez que « Marketing » est maintenant inséré à plusieurs endroits du script.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Créer des modèles personnalisés](lesson-3-2-create-custom-templates.md)  
  
  
